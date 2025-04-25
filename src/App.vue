<script setup>

<<<<<<< HEAD
const produtos = [
    { id: 1, capa: '/img/Chain_of_Iron_Vol.2.png', titulo: 'Chain of Iron: Volume 2', autor: 'Cassandra Clare', preco: '23.24'},
    { id: 2, capa: '/img/Chain_of_Thorns.png', titulo: 'Chain of Thorns', autor: 'Cassandra Clare', preco: '23.24'},
    { id: 3, capa: '/img/City_of_Fallen_Angels.png', titulo: 'City of Fallen Angels', autor: 'Cassandra Clare', preco: '13.94'},
    { id: 4, capa: '/img/Nona_the_Ninth.png', titulo: 'Nona the Ninth', autor: 'Cassandra Clare', preco: '16.84'},
    { id: 5, capa: '/img/Harlem_Shuffle.png', titulo: 'Harlem Shuffle', autor: 'Colson Whitehead', preco: '26.92'},
    { id: 6, capa: '/img/Two_Old_Women.png', titulo: 'Two Old Women', autor: 'Velma Wallis', preco: '13.95'},
    { id: 7, capa: '/img/Carrie_Soto_Is_Back.png', titulo: 'Carrie Soto Is Back', autor: 'Taylor Jenkins Reid', preco: '26.04'},
    { id: 8, capa: '/img/Book_Lovers.png', titulo: 'Book Lovers', autor: 'Emily Henry', preco: '15.81'},
  ];
</script>

<template>
  <header>
    <p>IFbooks<span class="IFbook"></span></p>
    <p class="apreco_leitura">Apreço a <br>
        leitura</p>
        <div id="divPesquisa">
          <input type="text" id="textotBarraDePesquisa" placeholder="Pesquisar" />
          <button id="lupa" aria-label="Pesquisar"><span class="fa-solid fa-magnifying-glass"></span></button>
        </div> 
    <nav>
      <ul>
        <li><a href="#"></a>Termos</li>
        <li><a href="#"></a>Equipe</li>
        <li><a href="#"></a>Envio</li>
        <li><a href="#"></a>Devoluções</li>
        <li><span class="fa-solid fa-cart-shopping icone"></span></li>
        <li><span class="fa-solid fa-heart icone"></span></li>
        <li><span class="fa-solid fa-user icone-user"></span></li>
      </ul>
    </nav>

  </header>
  <main>
    <section class="banner"> 
      <div class="introducaoBanner">
        <p><span>Autor de Abril</span></p>
        <h1>Eric-Emanuel Schmitt</h1>
        <p>Eric-Emmanuel Schmitt has been awarded more than 20 literary prizes and distinctions, and in 2001 he received the title of Chevalier des Arts et des Lettres. His books have been translated into over 40 languages.</p>
        <button>Acessar página do livro</button>
      </div> 
      <div class="capaLivro">
        <img src="/img/livroBanner.png" alt="Livro do banner">
        <p>*within the stock limit</p>
      </div>
    </section>
    <section class="informacoes">

    </section> 
    <section class="lancamentos">
      <h2>Lançamentos</h2>
      <ul>
        <li v-for="produto in produtos" :key="produto.id">
        <img :src="produto.capa" alt="Capa do livro" />
        {{ produto.titulo }} {{ produto.autor }} {{ 'R$ ' + Number(produto.preco).toFixed(2).replace('.', ',') }}
        </li>
      </ul>
    </section>
  </main>
  <footer>
  <div class="footer">
    <div class="esquerdo">
      <p class="logo">IFbooks</p>
      <ul class="icones">
        <li><span class="fa-brands fa-square-facebook" style="color: #ffffff;"></span></li>
        <li><span class="fa-brands fa-instagram" style="color: #ffffff;"></span></li>
        <li><span class="fa-brands fa-square-twitter" style="color: #ffffff;"></span></li>
      </ul>
    </div>
    <div class="direito">
      <div class="contato">
        <p>Contato</p>
        <p>
          <span class="fa-solid fa-phone" style="color: #FFFFFFCC;"></span> +55 47 40045263<br>
          <span class="fa-solid fa-clock" style="color: #FFFFFFCC;"></span> 8h às 23h - Seg a Sex<br>
          <span class="fa-solid fa-envelope" style="color: #FFFFFFCC;"></span> contato@ifbooks.com
        </p>
      </div>
      <div class="cartoes">
        <img src="/img/paypal_card.png" alt="Cartão PAYPAL">
        <img src="/img/Master_card.png" alt="Cartão MasterCard">
        <img src="/img/VISA_card.png" alt="Cartão VISA">
      </div>
    </div>
  </div>
  <p class="direitos">&copy; Alguns direitos reservados. IFbooks 2025.</p>
</footer>
</template>

<style scoped>
/*HEADER*/
#divPesquisa {
  position: relative;
  display: inline-block;
}
#textotBarraDePesquisa {
  padding-right: 35px; /* espaço pra lupa não ficar em cima do texto */
  width: 376.52px;
  height: 36.05px;
  top: 18.03px;
  left: 322.45px;
  border: 1px solid #F1F1F1;
  border-radius: 2px;
  background-color: #F1F1F1;
  color: #000000;
  font-family: Arial, Helvetica, sans-serif;
}
#lupa {
  position: absolute;
  right: 5px;
  top: 50%;
  transform: translateY(-50%);
  background: transparent;
  border: none;
  cursor: pointer;
  color: #231F2D;
  font-size: 16px;
}
header {
  display: flex;
  margin: 2vw 2vw 2vw 3vw;
  border-bottom: 1px solid #27AE60;
}
header p {
  text-align: center; 
}
header span.IFbook {
  border-right: 1px solid #27AE60;
  margin: 1vw ;
}
header p.apreco_leitura {
  color: #27AE60;
  margin: 0 2vw 0 0;
}
header ul {
  display: flex;
}
header nav ul li {
  margin: 10px 30px 10px 30px;
}
.icone {
  color: #27AE60;
  border-right: 1px solid #27AE60;
}
.icone-user {
  color: #27AE60;
}

/*MAIN*/

div.capaLivro {
  border-bottom: 1px solid #27AE60;
}
div.introducaoBanner span {
  border: 1px solid #27AE60;
  padding: 10.01px;
  border-radius: 3px;
  color: #27AE60;
}
.lancamentos {
  padding: 0 0 15vw 0;
}

/*FOOTER*/
.footer {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 20px;
  background-color: #27AE60;
  color: white;
}
.esquerdo {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.direito {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.logo {
  font-size: 1.5rem;
  font-weight: bold;
}
.icones {
  list-style: none;
  display: flex;
  gap: 15px;
  padding: 0;
  margin: 0;
}
.contato p {
  margin: 0;
  line-height: 1.6;
}
.cartoes img {
  width: 50px;
  margin-right: 10px;
}
.direitos {
  text-align: center;
  padding: 15px;
  font-size: 0.9rem;
  background-color: #27AE60; 
  color: #FFFFFF99;
}
=======
</script>

<template>
  <h1></h1>
</template>

<style scoped>

>>>>>>> 6bb6837bd3384d04f7ca12c657de7d711d88d954
</style>
