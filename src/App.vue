<script setup>
const produtos = [
    {
        id: 1,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Chain of Iron: Volume 2',
        autor: 'Cassandra Clare',
        preco: 23.24,
    },
    {
        id: 2,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Chain of Thorns',
        autor: 'Cassandra Clare',
        preco: 23.24,
    },
    {
        id: 3,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'City of Fallen Angels',
        autor: 'Cassandra Clare',
        preco: 13.94,
    },
    {
        id: 4,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Nona the Ninth',
        autor: 'Cassandra Clare',
        preco: 16.84,
    },
    {
        id: 5,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Harlem Shuffle',
        autor: 'Colson Whitehead',
        preco: 26.92,
    },
    {
        id: 6,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Two Old Women',
        autor: 'Velma Wallis',
        preco: 13.95,
    },
    {
        id: 7,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Carrie Soto Is Back',
        autor: 'Taylor Jenkins Reid',
        preco: 26.04,
    },
    {
        id: 8,
        capa: 'https://placehold.co/600x400.png',
        titulo: 'Book Lovers',
        autor: 'Emily Henry',
        preco: 15.81,
    },
];

const items = [
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
    <p>IFbooks <span>|</span></p>
    <p>Apreço a <br>
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
        <li><span class="fa-solid fa-cart-shopping" style="color: #26a269;">|</span></li>
        <li><span class="fa-solid fa-heart" style="color: #26a269;">|</span></li>
        <li><span class="fa-solid fa-user" style="color: #26a269;"></span></li>
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
        <li v-for="item in items" :key="item.id">
        <img :src="item.capa" alt="Capa do livro" />
        {{ item.titulo }} {{ item.autor }} {{ 'R$ ' + Number(item.preco).toFixed(2).replace('.', ',') }}
        </li>
      </ul>
    </section>
  </main>
  <footer>
    <div>
      <p>IFbooks</p>
      <ul>
        <li><span class="fa-brands fa-square-facebook" style="color: #ffffff;"></span></li>
        <li><span class="fa-brands fa-instagram" style="color: #ffffff;"></span></li>
        <li><span class="fa-brands fa-square-twitter" style="color: #ffffff;"></span></li>
      </ul>
    </div>
    <div>
      <p>Contato</p>
      <span class="fa-solid fa-phone" style="color: #FFFFFFCC;"></span> +55 47 40045263
      <span class="fa-solid fa-clock" style=" color: #FFFFFFCC;"></span> 8h às 23h - Seg a Sex
      <span class="fa-solid fa-envelope" style=" color: #FFFFFFCC;"></span> contato@ifbooks.com
    </div>
    <div>
      <img src="/img/paypal_card.png" alt="Cartão PAYPAL">
      <img src="/img/Master_card.png" alt="Cartão MasterCard">
      <img src="/img/VISA_card.png" alt="Cartão VISA">
    </div>
    <p>&copy; Alguns direitos reservados. IFbooks 2025. </p>
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

/*MAIN*/

div.introducaoBanner span {
  border: 1px solid #27AE60;
  padding: 10.01px;
  border-radius: 3px;
  color: #27AE60;
}

/*FOOTER*/

footer {
  background-color: #27AE60;
}
</style>
