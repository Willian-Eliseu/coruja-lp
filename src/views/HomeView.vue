<script setup>
// ---images---
import Logo from '@/assets/img/logo.png'
import AreaAluno from '@/assets/img/area_aluno.png'

</script>

<template>
    <main>
        <!-- hero -->
        <section id="hero" class="align-content-center">
            <div class="container py-5">
                <div class="row">
                    <div class="col-lg-9 col-xxl-6">
                        <img :src="Logo" alt="logomarca da corujá" width="240" class="mb-4" v-reveal="'bottom'">
                        <p class="fs-4 text-light fw-lighter mb-4" style="letter-spacing: 3px" v-reveal="'bottom'">
                            ELITE EM REVALIDAÇÃO MÉDICA
                        </p>
                        <h1 class="mb-4" v-reveal="'bottom'">
                            <span class="text-warning">Revalide seu diploma médico em Portugal ou prepare-se para a
                                PNA</span> <span class="text-light">com quem teve as maiores notas da história do
                                concurso</span>
                        </h1>
                        <p class="fs-5 mb-4 text-light" v-reveal="'bottom'">
                            Tudo o que você precisa para se preparar com segurança, foco e resultados. O <span
                                class="fw-semibold">método validado por mais de 800 médicos aprovados.</span>
                        </p>
                        <!-- falta a configuração do clique -->
                        <button class="btn btn-danger py-3 px-5 btn-lg mb-4">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- o que é a corujá mentoria -->
        <section>
            <div class="container py-5">
                <div class="row mb-4">
                    <div class="col" v-reveal="'bottom'">
                        <h1 class="text-danger text-center fw-bold">O que é a CoruJÁ Mentoria?</h1>
                    </div>
                </div>
                <div class="row mb-4">
                    <div class="col-lg-6 align-self-center">
                        <p class="fs-5 mb-3" v-reveal="'bottom'">
                            É um programa completo de preparação para médicos que desejam revalidar o diploma em
                            Portugal, focado na 1ª e 2ª fase da prova de Equivalência Médica e PNA.
                        </p>
                        <p class="fs-5" v-reveal="'bottom'">
                            Todo o conteúdo foi estruturado por dois médicos brasileiros que tiveram as maiores notas da
                            história da revalidação. Por todos esses motivos e benefícios, <span
                                class="fw-semibold text-success">somos a mentoria mais recomendada e com os maiores
                                índices de aprovações do mercado.</span>
                        </p>
                    </div>
                    <div class="col-lg-6 align-self-center">
                        <img :src="AreaAluno" alt="imagem da área do aluno" class="img-fluid" v-reveal="'bottom'">
                    </div>
                </div>
                <div class="row">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg mb-4">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- esta mentoria é para você que -->
        <section></section>

        <!-- decisões baseadas em evidências -->
        <section></section>

        <!-- apresentação dos doutores -->
        <section></section>

        <!-- por que a corujá é diferente? -->
        <section></section>

        <!-- depoimentos dos nossos alunos -->
        <section></section>

        <!-- a preparação mais completa -->
        <section></section>

        <!-- dúvidas frequentes -->
        <section></section>
    </main>
</template>

<style scoped>
#hero {
    background-image: url(../assets/img/hero.png);
    background-position: center left;
    background-repeat: no-repeat;
    background-size: cover;
    min-height: 600px;
}

@media screen and (min-width: 1200px) {
    #hero {
        min-height: 88dvh;
    }
}
</style>