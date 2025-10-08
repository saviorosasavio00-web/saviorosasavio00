<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Painel de Estatísticas</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 900px;
      margin: 30px auto;
      padding: 20px;
      background-color: #f5f5f5;
    }
    h1 {
      text-align: center;
      margin-bottom: 40px;
    }
    .chart-container {
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      margin-bottom: 40px;
    }
  </style>
</head>
<body>

  <h1>Painel de Estatísticas</h1>

  <div class="chart-container">
    <h2>Usuários Ativos (Últimos 6 meses)</h2>
    <canvas id="usuariosChart"></canvas>
  </div>

  <div class="chart-container">
    <h2>Distribuição de Tecnologias</h2>
    <canvas id="tecnologiasChart"></canvas>
  </div>

  <script>
    // Gráfico de linhas para usuários ativos
    const ctxUsuarios = document.getElementById('usuariosChart').getContext('2d');
    const usuariosChart = new Chart(ctxUsuarios, {
      type: 'line',
      data: {
        labels: ['Mai', 'Jun', 'Jul', 'Ago', 'Set', 'Out'],
        datasets: [{
          label: 'Usuários Ativos',
          data: [120, 150, 170, 140, 180, 200],
          borderColor: 'rgba(75, 192, 192, 1)',
          backgroundColor: 'rgba(75, 192, 192, 0.2)',
          fill: true,
          tension: 0.3,
          pointRadius: 5,
          pointHoverRadius: 7,
        }]
      },
      options: {
        responsive: true,
        scales: {
          y: {
            beginAtZero: true,
            stepSize: 20
          }
        }
      }
    });

    // Gráfico de pizza para tecnologias
    const ctxTecnologias = document.getElementById('tecnologiasChart').getContext('2d');
    const tecnologiasChart = new Chart(ctxTecnologias, {
      type: 'doughnut',
      data: {
        labels: ['JavaScript', 'Python', 'Java', 'C#', 'Outros'],
        datasets: [{
          label: 'Uso de Tecnologias',
          data: [45, 25, 15, 10, 5],
          backgroundColor: [
            'rgba(255, 206, 86, 0.7)',
            'rgba(54, 162, 235, 0.7)',
            'rgba(255, 99, 132, 0.7)',
            'rgba(153, 102, 255, 0.7)',
            'rgba(201, 203, 207, 0.7)'
          ],
          borderColor: 'white',
          borderWidth: 2,
        }]
      },
      options: {
        responsive: true,
        cutout: '70%',
        plugins: {
          legend: {
            position: 'right',
          }
        }
      }
    });
  </script>

</body>
</html>

