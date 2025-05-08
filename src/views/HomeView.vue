<script setup>
import { ref } from 'vue'

const currentDate = ref(new Date().toLocaleDateString())
</script>

<template>
  <div class="home">
    <h1>Dashboard</h1>
    <p class="date">{{ currentDate }}</p>

    <div class="dashboard-grid">
      <div class="card dashboard-card">
        <h3>Vendas do Mês</h3>
        <div class="card-content">
          <p class="stat">R$ 45.890,00</p>
          <p class="change positive">+15% em relação ao mês anterior</p>
        </div>
      </div>

      <div class="card dashboard-card">
        <h3>Novos Clientes</h3>
        <div class="card-content">
          <p class="stat">124</p>
          <p class="change positive">+22 em relação ao mês anterior</p>
        </div>
      </div>

      <div class="card dashboard-card">
        <h3>Pedidos em Aberto</h3>
        <div class="card-content">
          <p class="stat">38</p>
          <p class="change neutral">0 em relação à semana anterior</p>
        </div>
      </div>

      <div class="card dashboard-card">
        <h3>Itens de Baixo Estoque</h3>
        <div class="card-content">
          <p class="stat">12</p>
          <p class="change negative">+3 em relação à semana anterior</p>
        </div>
      </div>
    </div>

    <div class="card">
      <h2>Pedidos Recentes</h2>
      <table class="data-table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Cliente</th>
            <th>Valor</th>
            <th>Status</th>
            <th>Data</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>#4829</td>
            <td>Maria Silva</td>
            <td>R$ 578,90</td>
            <td><span class="status-badge shipped">Enviado</span></td>
            <td>12/04/2025</td>
          </tr>
          <tr>
            <td>#4828</td>
            <td>João Oliveira</td>
            <td>R$ 1.245,00</td>
            <td><span class="status-badge processing">Em processamento</span></td>
            <td>11/04/2025</td>
          </tr>
          <tr>
            <td>#4827</td>
            <td>Ana Costa</td>
            <td>R$ 367,50</td>
            <td><span class="status-badge delivered">Entregue</span></td>
            <td>10/04/2025</td>
          </tr>
          <tr>
            <td>#4826</td>
            <td>Carlos Mendes</td>
            <td>R$ 890,25</td>
            <td><span class="status-badge cancelled">Cancelado</span></td>
            <td>09/04/2025</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.home {
  padding: 1rem;
}

.date {
  color: var(--color-text-muted);
  margin-bottom: 2rem;
}

.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.dashboard-card {
  padding: 1.5rem;
}

.dashboard-card h3 {
  margin-bottom: 1rem;
  color: var(--color-heading);
}

.card-content {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.stat {
  font-size: 1.8rem;
  font-weight: bold;
}

.change {
  font-size: 0.9rem;
}

.positive {
  color: #2ecc71;
}

.negative {
  color: #e74c3c;
}

.neutral {
  color: #7f8c8d;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
}

.data-table th,
.data-table td {
  padding: 0.75rem;
  text-align: left;
  border-bottom: 1px solid var(--color-border);
}

.data-table th {
  font-weight: bold;
  color: var(--color-heading);
}

.status-badge {
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  font-size: 0.8rem;
  font-weight: bold;
}

.shipped {
  background-color: #3498db;
  color: white;
}

.processing {
  background-color: #f39c12;
  color: white;
}

.delivered {
  background-color: #2ecc71;
  color: white;
}

.cancelled {
  background-color: #e74c3c;
  color: white;
}
</style>
