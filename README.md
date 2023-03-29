# Merkle-tree 
const crypto = require('crypto');

// Lista de nombres
const lista_nombres = ['Juan', 'Maria', 'Pedro', 'Sofia'];

// Calcula el hash de cada nombre y lo almacena en un objeto
const hashes_nombres = {};
lista_nombres.forEach((nombre) => {
  const hash_nombre = crypto.createHash('sha256').update(nombre).digest('hex').slice(0, 8);
  hashes_nombres[hash_nombre] = true;
});

// Función para verificar si un nombre está en la lista
function esta_en_lista(nombre) {
  const hash_nombre = crypto.createHash('sha256').update(nombre).digest('hex').slice(0, 8);
  return hash_nombre in hashes_nombres;
}

// Ejemplo de uso
const nombre_a_verificar = 'Juan';
if (esta_en_lista(nombre_a_verificar)) {
  console.log(`${nombre_a_verificar} está en la lista`);
} else {
  console.log(`${nombre_a_verificar} no está en la lista`);
}
