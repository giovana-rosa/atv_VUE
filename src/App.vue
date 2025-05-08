<script setup>
import { ref, computed, reactive } from 'vue'

const produtos = ref([
  { 
    id: 1,
    capa: '/img/Chain_of_Iron_Vol.2.png',
    titulo: 'Chain of Iron: Volume 2',
    autor: 'Cassandra Clare',
    preco: 23.24,
    favorito: false     
  },
  { 
    id: 2,
    capa: '/img/Chain_of_Thorns.png',
    titulo: 'Chain of Thorns',
    autor: 'Cassandra Clare',
    preco: 23.24,
    favorito: false
  },
  { 
    id: 3,
    capa: '/img/City_of_Fallen_Angels.png',
    titulo: 'City of Fallen Angels',
    autor: 'Cassandra Clare', 
    preco: 13.94,
    favorito: false
  },
  { 
    id: 4,
    capa: '/img/Nona_the_Ninth.png', 
    titulo: 'Nona the Ninth', 
    autor: 'Cassandra Clare', 
    preco: 16.84,
    favorito: false
  },
  { 
    id: 5, 
    capa: '/img/Harlem_Shuffle.png', 
    titulo: 'Harlem Shuffle', 
    autor: 'Colson Whitehead', 
    preco: 26.92,
    favorito: false
  },
  { 
    id: 6, 
    capa: '/img/Two_Old_Women.png', 
    titulo: 'Two Old Women', 
    autor: 'Velma Wallis', 
    preco: 13.95,
    favorito: false
  },
  { 
    id: 7, 
    capa: '/img/Carrie_Soto_Is_Back.png', 
    titulo: 'Carrie Soto Is Back', 
    autor: 'Taylor Jenkins Reid', 
    preco: 26.04,
    favorito: false
  },
  { 
    id: 8, 
    capa: '/img/Book_Lovers.png', 
    titulo: 'Book Lovers', 
    autor: 'Emily Henry', 
    preco: 15.81,
    favorito: false
  }
]);


function alternarFavorito(produto) {
  produto.favorito = !produto.favorito
}

const carrinho = reactive({
    items: [
   
    ],
    frete: 0,
    desconto: 0,
    total: 0,
});


function adicionarCarrinho(idItem) {
  console.log(idItem);

  let livro = produtos.value.find(({ id }) => id == idItem);

  console.log(livro)

  let itemNoCarrinho = carrinho.items.find(item => item.id === idItem);

  if (itemNoCarrinho) {
    itemNoCarrinho.quantidade += 1;
    itemNoCarrinho.valorTotal = itemNoCarrinho.quantidade * itemNoCarrinho.preco;
  } else {
    carrinho.items.push({
      id: idItem,
      capa: livro.capa,
      titulo: livro.titulo,
      autor: livro.autor,
      preco: livro.preco,
      quantidade: 1,
      valorTotal: livro.preco
    });
  }

  console.log(carrinho);
}

const contador = ref(0)

function incrementar() {
  contador.value++
}

function decrementar() {
  if (contador.value > 0) {
    contador.value--
  }
}

function calcularValorTotal() {
  let total = 0;
  carrinho.items.forEach(item => {
    total += item.valorTotal;
  });
  return total;
}

</script>

<template>
  <header>
    <p>IFbooks<span class="IFbook"></span></p>
    <p class="apreco_leitura">Apreço a <br> leitura</p>
        <div id="divPesquisa">
          <input type="text" id="textotBarraDePesquisa" placeholder="Pesquisar" />
          <button id="lupa" aria-label="Pesquisar"><span class="fa-solid fa-magnifying-glass"></span></button>
        </div> 
    <nav>
      <ul>
        <li><a href="#">Termos</a></li>
        <li><a href="#">Equipe</a></li>
        <li><a href="#">Envio</a></li>
        <li><a href="#">Devoluções</a></li>
        <li><a href="#carrinhoBanner"><span class="fa-solid fa-cart-shopping icone"></span></a></li>
        <li><span class="fa-solid fa-heart icone"></span></li>
        <li><span class="fa-solid fa-user icone-user"></span></li>
      </ul>
    </nav>
  </header>
  
  <main>

    <section class="banner"> 
      <div class="introducaoBanner">
        <p class="autor_abril"><span>Autor de Abril</span></p>
        <h1>Eric-Emanuel Schmitt</h1>
        <p class="textoBanner">Eric-Emmanuet Schmitt has been awarded more than 20 literary prizes and distinctions, and in 2001 he received the title of Chevalier des Arts et des Lettres. His books have been translated into over 40 languages.</p>
        <button>Acessar página do livro</button>
      </div> 
      <div class="capaLivro">
        <img src="/img/livroBanner.png" alt="Livro do banner">
        <p class="paragrafoAbaixoDoLivroBanner">*within the stock limit</p>
      </div>
    </section>
    
    <section class="Informacao">
      <div class="iconesDeInformacao">
        <ul>
          <li class="linhaDivisoria"><span class="fa-solid fa-truck iconeInformacao"></span><a href="#">Frete grátis para SC</a></li>
          <li class="linhaDivisoria"><span  class="fa-solid fa-star iconeInformacao"></span><a href="#">Livros recomendados</a></li>
          <li class="linhaDivisoria"><span class="fa-solid fa-book-open iconeInformacaoBook"></span><a href="#">Mais vendidos</a></li>
        </ul>
      </div>
    </section> 

    <section id="lancamentos" class="lancamentos">
      <h2>Lançamentos</h2>
      <ul>
        <li v-for="produto in produtos" :key="produto.id">
          <article>
            <img :src="produto.capa" alt="Capa do livro" class="capaLancamentos"/>
            <h3 class="tituloProduto">{{ produto.titulo }}</h3>
            <p class="autorProduto">{{ produto.autor }}</p>
            <p class="precoProduto">{{ 'R$ ' + produto.preco.toFixed(2) }}<span :class="[produto.favorito ? 'fa-solid favorito' : 'fa-regular', 'fa-heart', 'iconeCoracao']" @click="alternarFavorito(produto)" style="cursor: pointer;"></span></p>
            <button class="botaoComprar" @click="adicionarCarrinho(produto.id)"><span class="fa-solid fa-cart-shopping" style="color: white;"></span> Comprar</button>
          </article>
        </li>
      </ul>
    </section>

    <section id="carrinhoBanner" class="carrinhoBanner">
    <h2>Carrinho</h2>
    <div class="informacoesCarrinhos">
      <h3>Título</h3>
      <ul>
        <li v-for="produto in carrinho.items" :key="produto.id">
          <article>
            <div>
              <div>
                <img :src="produto.capa" alt="Capa do livro" class="capaLancamentos"/>
              </div>
              <div class="informacoesProdutosCarrinho">
                <h3 class="tituloProduto">{{ produto.titulo }}</h3>
                <p class="autorProduto">{{ produto.autor }}</p>
                <p class="precoProduto"> {{ 'R$ '+ produto.preco.toFixed(2)}}</p>
              </div>
            </div>
          </article>
        </li>
      </ul>  
        <h3 class="carrinhoQuantidade">Quantidade</h3>
        <button v-on:click="incrementar">+</button>
        <p>{{ contador }}</p>
        <button @click="decrementar">-</button>
      <h3>Subtotal</h3>
    </div>
  </section>

  <section class="carrinhoBotoes">
    <div class="funcionalidadesCarinho">
      <div>
        <button class="voltarLoja"><a href="#lancamentos">Voltar para loja</a></button>
      </div>
      <div>
        <input type="text" id="cupomDeDesconto" placeholder="Código do cupom" />
        <button class="inserirCupom">Inserir Cupom</button>
      </div>
      <div class="totalDaCompraCarrinho">
        <p class="totalCompra">Total da Compra</p>
        <p class="produtos">Produtos:</p>
        <p class="frete">Frete:</p>
        <p>Total:</p>
        <button>Ir para o pagamento</button>
      </div>
    </div>
  </section>
   
  </main>
  <footer>
  <div class="footer">
    <div class="esquerdo">
      <p class="logo">IFbooks</p>
      <ul class="icones">
        <li><a href="https://www.facebook.com/?locale=pt_BR"><span class="fa-brands fa-square-facebook" style="color: #ffffff;"></span></a></li>
        <li><a href="https://www.instagram.com/"><span class="fa-brands fa-instagram" style="color: #ffffff;"></span></a></li>
        <li><a href="https://x.com/?lang=pt"><span class="fa-brands fa-square-twitter" style="color: #ffffff;"></span></a></li>
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

/* GERAL */

html {
  scroll-behavior: smooth;
}
p, h1, h2, h3, h4, h5, h6 {
  font-family: Arial, Helvetica, sans-serif;
}
section.Informacao div ul li a {
  font-family: Arial, Helvetica, sans-serif;
}
button {
  cursor: pointer;
  font-family: Arial, Helvetica, sans-serif;
}

/*HEADER*/

hr {
color: #27AE60;
}
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
  padding: 2vw 2vw 2vw 3vw;
  justify-content: center;
  border-bottom: 1px solid #27AE60;
}
header p div {
  border-bottom: 1px solid #27AE60;
}
header p {
  text-align: center; 
}
header span.IFbook {
  border-right: 1px solid #27AE60;
  margin: 0 0 0 10px;
}
header p.apreco_leitura {
  color: #27AE60;
  margin: 0 20px 0 10px;
}
header ul {
  display: flex;
}
header nav ul li {
  margin: 10px 30px 10px 30px;
}
header nav ul li a {
  text-decoration: none;
  color: #7b7881;
}
.icone {
  color: #27AE60;
  border-right: 1px solid #27AE60;
}
.icone-user {
  color: #27AE60;
}

/*MAIN*/

section.banner  {
  display: flex;
}
section.banner h1 {
  font-weight: bold;
}
div.introducaoBanner span {
   border: 1px solid #27AE60;
  padding: 10.01px;
  border-radius: 3px;
  color: #27AE60;
}
section.banner div.introducaoBanner p.autor_abril {
  margin: 8vw 2vw 3vw 17vw;
}
section.banner div.introducaoBanner h1 {
  font-size: 48px;
  margin: 0 2vw 0 17vw;
}
section.banner div.introducaoBanner p.textoBanner {
  color: #4D4C4C;
  font-size: 16px;
  margin: 3vw 0 3vw 17vw;
  width: 477.6625061035156px;
  line-height: 24.03px;
  letter-spacing: 0%;
  font-weight: 400;
}
section.banner div.introducaoBanner button {
  color: white;
  width: 243.08889770507812px;
  height: 49.03333282470703px;
  top: 516.85px;
  left: 164.23px;
  border-radius: 2px;
  padding-top: 12.02px;
  padding-right: 32.04px;
  padding-bottom: 12.02px;
  padding-left: 32.04px;
  gap: 10.01px;
  background-color: #27AE60;
  margin: 0 2vw 0 17vw;
  border: none;
}
section.banner div.capaLivro img {
  margin: 0 0 0 10vw;
} 
section.carrinho div {
  border-bottom: 1px solid #27AE60;
}
section.banner div.capaLivro .paragrafoAbaixoDoLivroBanner {
  width: 168.23333740234375px;
  height: 25px;
  top: 586.95px;
  left: 1150.61px;
  font-size: 16px;
  margin: 0 0 2vw 25vw;
}
section.Informacao div.icone-book p span  {
  width: 38.453304290771484px;
  height: 33.646644592285156px;
  top: 9.61px;
  left: 4.81px;
}
section.Informacao {
  border-top: 1px solid #27AE60;
  border-bottom: 1px solid #27AE60;
  padding: 4vw 0 4vw 0;
}
section.Informacao div ul li { /* N E G R I T O */
  font-weight: bold;
}
.iconesDeInformacao ul   {
  display: flex;
}
.iconesDeInformacao ul li a {
  text-decoration: none;
  color: #000000;
  width: 279.3875427246094px;
  height: 33px;
  top: 734.22px;
  left: 637.88px;
  font-size: 22px;
} 
.iconesDeInformacao  span {
  font-size: 1.6rem;
  margin: 0 15px 0 16vw;
}
.iconeInformacaoBook {
  margin: 0 15px 0 16vw;
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
  gap: 15px;display: flex;
  margin: 2vw 2vw 2vw 3vw;
  justify-content: center;
}
.direitos {
  border-top: 1px solid #ffff;
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

/* LAÇAMENTOS */

section.lancamentos h2 {
  font-size: 40px;
  font-weight: bold;
  font-family: Arial, Helvetica, sans-serif;
  padding: 6vw 0 4vw 0;
}
section.lancamentos ul{
  display: flex;
  flex-wrap: wrap;
}
section.lancamentos ul li{
  width: 22%;
}
section.capaLancamentos {
  width: 274px;
  height: 414px;
  top: 1040px;
  left: 124px;
  border-radius: 3px;
}
section.lancamentos {
  margin: 0 0 0 7vw;
}
section.lancamentos .tituloProduto, .precoProduto {
  font-weight: bold;
}
section.lancamentos img, h3, p, p, button {
  padding: 0.8vw 0 0.8vw 0;
}
section.lancamentos button {
  margin: 0 0 6.5vw 0;
}
section.lancamentos button.botaoComprar {
  width: 274px;
  height: 48px;
  top: 1617px;
  left: 1042px;
  border-radius: 2px;
  background-color: #27AE60;
  color: white;
  border: none;
}

/*CARINHO*/

.linhaDivisoria {
  border-left: 1px solid #ccc;
  padding-left: 10px;
  margin-left: 10px;
}
section.carrinhoBanner h2 {
  color: #27AE60;
  font-size: 38px;
  margin: 7vw 0 0 14vw;
}
section.carrinhoBanner .informacoesCarrinhos {
  display: flex;
  font-size: 24px;
  border-bottom: 1px solid #27AE60;
  margin: 3vw 14vw 5vw;
}
section.carrinhoBanner .informacoesCarrinhos  img {
  width: 94px;
  height: 142px;
  top: 496px;
  left: 155px;
  border-radius: 3px;
}
section.carrinhoBanner .informacoesCarrinhos div {
  display: flex;
}
section.carrinhoBanner .informacoesCarrinhos .informacoesProdutosCarrinho {
  display: block;
  margin: 0 0 0 1vw;
}
section.carrinhoBanner .informacoesCarrinhos h3.carrinhoQuantidade {
  margin: 0 25vw 0 30vw;
}
section.carrinhoBotoes .funcionalidadesCarinho button.voltarLoja {
  background-color: white;
  border: none;
  border: 1px solid #000000;
  padding: 0.8vw 2vw 0.8vw 2vw;
  border-radius: 4px;
  margin: 0 13vw 2vw 13vw;
}
section.carrinhoBotoes .funcionalidadesCarinho button.voltarLoja a {
  text-decoration: none;
  color: #000000;
  font-size: 1.3rem;
}
section.carrinhoBotoes div input {
  padding: 0.8vw 2vw 0.8vw 1.4vw;
  margin: 0 1vw 0 13vw;
  border: 1px solid #000000;
  border-radius: 4px;
}
section.carrinhoBotoes button.inserirCupom {
  border: 1px solid #27AE60;
  background-color: #27AE60;
  padding: 0.8vw 1.5vw 0.8vw 1.5vw;
  text-decoration: none;
  color: white;
  border-radius: 4px;
}
 section.carrinhoBotoes div.totalDaCompraCarrinho {
  border: 1px solid #000000;
  width: 470px;
  height: 324px;
  margin: 0 0 3vw 65vw;
} 

section.carrinhoBotoes div.totalDaCompraCarrinho  p {
  margin: 1vw 1vw 0 1vw;
}
section.carrinhoBotoes div.totalDaCompraCarrinho p.totalCompra {
  font-size: 1vw;
}

section.carrinhoBotoes div.totalDaCompraCarrinho p.produtos {
  border-bottom: 1px solid #000000;
}

section.carrinhoBotoes div.totalDaCompraCarrinho p.frete {
  border-bottom: 1px solid #000000;
}

section.carrinhoBotoes div.totalDaCompraCarrinho button {
  border: 1px solid #27AE60;
  background-color: #27AE60;
  padding: 0.8vw 1.5vw 0.8vw 1.5vw;
  text-decoration: none;
  color: white;
  border-radius: 4px;
  margin: 1vw 1vw 0 6vw;
}

.favorito {
  color: #27AE60;
}
.iconeCoracao {
  color: #27AE60;
}
</style>
