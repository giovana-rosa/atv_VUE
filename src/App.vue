<script setup>

</script>

<template>
  <header>
    <p>IFbooks <span>|</span></p>
    <p>Apreço a <br>
        leitura</p>
    <div id="divPesquisa">
      <input type="text" id="txtPesquisa" placeholder="Pesquisar"/>
      <span class="fa-solid fa-magnifying-glass" style=" color: #231F2D;" id="btnPesquisa" alt="Pesquisa"></span> 
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
        <img src="../public/img/livroBanner.png" alt="Livro do banner">
        <p>*within the stock limit</p>
      </div>
    </section>
    <section class="informacoes">

    </section> 
    <section class="lancamentos">
      <h2>Lançamentos</h2>
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
      <img src="../public/img/paypal_card.png" alt="Cartão PAYPAL">
      <img src="../public/img/Master_card.png" alt="Cartão MasterCard">
      <img src="../public/img/VISA_card.png" alt="Cartão VISA">
    </div>
    <p>&copy; Alguns direitos reservados. IFbooks 2025. </p>
  </footer>
</template>

<style scoped>
/*HEADER*/





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
