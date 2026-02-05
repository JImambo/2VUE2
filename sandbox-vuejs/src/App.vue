<script setup lang="ts">
import { ref, computed } from 'vue'

const compteur = ref(0)

const statut = computed(() => {
  if (compteur.value > 0) return 'positif'
  if (compteur.value < 0) return 'negatif'
  return 'neutre'
})

const messageStatut = computed(() => {
  if (compteur.value > 0) return '✨ Positif'
  if (compteur.value < 0) return '⚠️ Négatif'
  return '⚪ Neutre'
})

function incrementer() { 
  compteur.value++ 
}

function decrementer() { 
  compteur.value-- 
}

function reset() { 
  compteur.value = 0 
}

function ajouterValeur(valeur: number) {
  compteur.value += valeur
}
</script>

<template>
  <div class="container">
    <div class="card">
      <h1 class="titre">Compteur</h1>
      
      <div class="affichage" :class="statut">
        <span class="valeur">{{ compteur }}</span>
      </div>
      
      <p class="statut" :class="statut">
        {{ messageStatut }}
      </p>
      
      <div class="boutons-principaux">
        <button @click="decrementer" class="btn btn-moins">
          <span class="icone">−</span>
          <span class="texte">Moins</span>
        </button>
        
        <button @click="reset" class="btn btn-reset">
          <span class="icone">↺</span>
          <span class="texte">Reset</span>
        </button>
        
        <button @click="incrementer" class="btn btn-plus">
          <span class="icone">+</span>
          <span class="texte">Plus</span>
        </button>
      </div>

      <div class="boutons-rapides">
        <button @click="ajouterValeur(-10)" class="btn-mini">-10</button>
        <button @click="ajouterValeur(-5)" class="btn-mini">-5</button>
        <button @click="ajouterValeur(5)" class="btn-mini">+5</button>
        <button @click="ajouterValeur(10)" class="btn-mini">+10</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.card {
  background: white;
  border-radius: 24px;
  padding: 40px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  max-width: 450px;
  width: 100%;
  text-align: center;
}

.titre {
  font-size: 2em;
  color: #333;
  margin-bottom: 30px;
  font-weight: 700;
}

.affichage {
  background: #f8f9fa;
  border-radius: 16px;
  padding: 30px;
  margin-bottom: 20px;
  transition: all 0.3s ease;
  border: 3px solid transparent;
}

.affichage.positif {
  background: linear-gradient(135deg, #d4fc79 0%, #96e6a1 100%);
  border-color: #4caf50;
}

.affichage.negatif {
  background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
  border-color: #f44336;
}

.affichage.neutre {
  background: linear-gradient(135deg, #e0e0e0 0%, #f5f5f5 100%);
  border-color: #9e9e9e;
}

.valeur {
  font-size: 4em;
  font-weight: 700;
  color: #333;
  display: block;
}

.statut {
  font-size: 1.3em;
  font-weight: 600;
  margin-bottom: 30px;
  padding: 10px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.statut.positif {
  color: #2e7d32;
  background: rgba(76, 175, 80, 0.1);
}

.statut.negatif {
  color: #c62828;
  background: rgba(244, 67, 54, 0.1);
}

.statut.neutre {
  color: #616161;
  background: rgba(158, 158, 158, 0.1);
}

.boutons-principaux {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
  margin-bottom: 20px;
}

.btn {
  padding: 16px 20px;
  font-size: 1.1em;
  font-weight: 600;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.2);
}

.btn:active {
  transform: translateY(0);
}

.btn-moins {
  background: linear-gradient(135deg, #ff6b6b 0%, #ee5a6f 100%);
  color: white;
}

.btn-moins:hover {
  background: linear-gradient(135deg, #ee5a6f 0%, #ff6b6b 100%);
}

.btn-reset {
  background: linear-gradient(135deg, #95a5a6 0%, #7f8c8d 100%);
  color: white;
}

.btn-reset:hover {
  background: linear-gradient(135deg, #7f8c8d 0%, #95a5a6 100%);
}

.btn-plus {
  background: linear-gradient(135deg, #51cf66 0%, #37b24d 100%);
  color: white;
}

.btn-plus:hover {
  background: linear-gradient(135deg, #37b24d 0%, #51cf66 100%);
}

.icone {
  font-size: 1.5em;
  font-weight: 700;
}

.texte {
  font-size: 0.85em;
}

.boutons-rapides {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  padding-top: 20px;
  border-top: 2px solid #e0e0e0;
}

.btn-mini {
  padding: 10px 15px;
  font-size: 0.95em;
  font-weight: 600;
  border: 2px solid #667eea;
  background: white;
  color: #667eea;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-mini:hover {
  background: #667eea;
  color: white;
  transform: scale(1.05);
}

.btn-mini:active {
  transform: scale(0.95);
}

@media (max-width: 500px) {
  .card {
    padding: 30px 20px;
  }
  
  .valeur {
    font-size: 3em;
  }
  
  .boutons-principaux {
    gap: 10px;
  }
  
  .btn {
    padding: 12px 15px;
  }
}
</style>