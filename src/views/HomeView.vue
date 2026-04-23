<script setup>
// ---images---
import Logo from '@/assets/img/logo.png'
import AreaAluno from '@/assets/img/area_aluno.png'
import CheckIcon from '@/assets/img/check_icon.png'
import CheckIcon2 from '@/assets/img/check_icon_2.png'
import JamilAnaAirplane from '@/assets/img/jamil_ana_airplane.png'
import Guarantee from '@/assets/img/guarantee.png'
import Lock from '@/assets/img/lock.png'
import BlackLogo from '@/assets/img/black_logo.png'

import alineMonteiro from '@/assets/img/aline_monteiro.webp'
import andreaNoronha from '@/assets/img/andrea_noronha.webp'
import cintiaPerico from '@/assets/img/cintia_perico.webp'
import deboraVeiga from '@/assets/img/debora.webp'
import geirizaChantre from '@/assets/img/geiriza_chantre.webp'
import mariaLeticia from '@/assets/img/maria_leticia.webp'
import nidiaChicralla from '@/assets/img/nidia_chicralla.webp'
import rebecaSpinelli from '@/assets/img/rebeca.webp'
import sergioCabral from '@/assets/img/sergio_cabral.webp'

import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';

import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';


const vantagensLista = [
    { id: 1, content: 'Está se preparando para revalidar o diploma médico em Portugal ou se preparando para a PNA' },
    { id: 2, content: 'Acabou de se formar ou já atua há anos na medicina' },
    { id: 3, content: 'Mora no Brasil, Portugal ou em outros países de língua portuguesa ou não, mas que deseja acessar o mercado de Portugal e Europa' },
    { id: 4, content: 'Está perdido(a) no meio de tanto conteúdo e não sabe por onde começar' },
    { id: 5, content: 'Quer estudar com segurança e orientação de perto por quem já passou pelo processo' },
    { id: 6, content: 'Deseja atuar como médico em Portugal ou simplesmente se atualizar com as práticas da medicina portuguesa e europeia' }
];

const dadosLista = [
    { id: 1, title: '+1000', content: 'Médicos aprovados' },
    { id: 2, title: '84%', content: 'Aprovação na 1ª Fase 2024' },
    { id: 3, title: '92%', content: 'Aprovação na 1ª Fase 2025' },
    { id: 4, title: '99%', content: 'Aprovação na 2ª Fase 2025' }
];

const diferencaLista = [
    { id: 1, icon: 'fa-solid fa-thumbtack', title: 'METODOLOGIA VALIDADA', content: 'Desenvolvida por quem já venceu o processo com as melhores notas, garantindo eficiência total no estudo.' },
    { id: 2, icon: 'fa-solid fa-lock', title: 'ESTRUTURA COMPLETA', content: 'Você não precisa buscar materiais fora. Tudo (teoria, questões e revisões) está centralizado na plataforma.' },
    { id: 3, icon: 'fa-solid fa-users', title: 'GRUPO DE APOIO CONTÍNUO', content: 'Não se sinta sozinho. Nosso grupo permite tirar dúvidas e ter contato direto com os mentores 24/7.' },
    { id: 4, icon: 'fa-solid fa-clock', title: 'FOCO NA 1ª E 2ª FASE', content: 'Preparamos você tanto para a teoria quanto para as avaliações práticas de forma integrada.' }
];

const faqItems = [
    {
        pergunta: "Preciso estar em Portugal para fazer a mentoria?",
        resposta: "Não. Todo o conteúdo é online e acessível de qualquer lugar."
    },
    {
        pergunta: "Serve para qualquer fase da revalidação?",
        resposta: "Atualmente, o foco é na 1ª fase. A mentoria da 2ª fase será lançada em breve na plataforma. Fique atento ao lançamento ou entre em contato."
    },
    {
        pergunta: "Como funciona o CoruJÁ Encontro?",
        resposta: "São encontros semanais ao vivo para tirar dúvidas e resolver as questões com maior índice de erros. Você pode assistir aos encontros ao vivo ou gravados."
    },
    {
        pergunta: "Quando começo a estudar?",
        resposta: "Assim que o pagamento for confirmado mediante comprovante de pagamento, o acesso é liberado automaticamente."
    },
    {
        pergunta: "Por quanto tempo tenho acesso?",
        resposta: "Você terá acesso por 12 meses, com possibilidade de renovação."
    }
];

const depoimentosList = [
    { id: 1, name: 'DRA. ALINE MONTEIRO', videoKey: 'yA3baoN7p2q9VfLc', img: alineMonteiro, tipo: 'Aluna CoruJÁ' },
    { id: 2, name: 'DRA. ANDRÉA NORONHA', videoKey: 'HzSrtNIm9ybzUL0P', img: andreaNoronha, tipo: 'Aluna CoruJÁ' },
    { id: 3, name: 'DRA. CÍNTIA PERICO', videoKey: 'Qzzlnnbp7rCi8xpz', img: cintiaPerico, tipo: 'Aluna CoruJÁ' },
    { id: 4, name: 'DRA. DÉBORA VEIGA', videoKey: 'X2ySnvT1wFUim2uv', img: deboraVeiga, tipo: 'Aluna CoruJÁ' },
    { id: 5, name: 'DRA. GEIRIZA CHANTRE', videoKey: 'OK6UXigw69H6M5hb', img: geirizaChantre, tipo: 'Aluna CoruJÁ' },
    { id: 6, name: 'DRA. MARIA LETÍCIA', videoKey: 'pIF4TbCOcePiHkGp', img: mariaLeticia, tipo: 'Médica validada em Portugal' },
    { id: 7, name: 'DRA. NIDIA CHICRALLA', videoKey: 'LrUDNUwclZLgdS3o', img: nidiaChicralla, tipo: 'Aluna CoruJÁ' },
    { id: 8, name: 'DRA. REBECA SPINELLI', videoKey: 'SQVOdX4MQEDF9gBn', img: rebecaSpinelli, tipo: 'Aluna CoruJÁ' },
    { id: 9, name: 'DR. SÉRGIO CABRAL', videoKey: '5RAc5SiHPF8mcU3G', img: sergioCabral, tipo: 'Aluno CoruJÁ' },
];

const modalVideo = ref(null);
const currentPlayerUrl = ref('');
const currentDoctorName = ref('');

const openPlayer = (videoKey, doctorName) => {
    currentDoctorName.value = doctorName;
    currentPlayerUrl.value = `https://cdn.tbr.com.br/player/?vod=1&video=${videoKey}&dual_audio=0`;
    modalVideo.value.showModal();
}

const closeModal = () => {
    modalVideo.value.close();
    currentPlayerUrl.value = '';
}

const modules = [Navigation, Pagination, Autoplay];

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
                        <button class="btn btn-danger py-3 px-5 btn-lg mb-4 effect-3">
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
                        <button class="btn btn-danger py-3 px-5 btn-lg mb-4 effect-3">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- esta mentoria é para você que -->
        <section style="background-color: #032612">
            <div class="container py-5">
                <div class="row mb-4">
                    <h1 class="text-light text-center fw-bold" v-reveal="'bottom'">
                        Esta mentoria é para você que
                    </h1>
                </div>
                <div class="row mb-4">
                    <div class="col-md-6 col-lg-4 mb-4" v-for="i in vantagensLista" :key="i.id">
                        <div class="p-3 rounded-3 box-height-1 effect-1" style="border: solid 1px #14AE5C;"
                            v-reveal="'bottom'">
                            <img :src="CheckIcon" alt="ícone" class="d-block mb-3" width="50" height="50">
                            <p class="text-light fs-5 fw-light">
                                {{ i.content }}
                            </p>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- decisões baseadas em evidências -->
        <section>
            <div class="container py-5">
                <div class="row mb-4">
                    <h1 class="text-center mb-3" v-reveal="'bottom'" style="color: #032612">
                        Decisões baseadas em evidências
                    </h1>
                    <p class="text-center fs-5" v-reveal="'bottom'">
                        Como médicos, baseamos nossas condutas em fatos.
                        <br>
                        O mesmo deve ser feito com sua carreira.
                    </p>
                </div>
                <div class="row mb-4">
                    <div class="col-lg-6 mb-3 mb-lg-0" v-reveal="'bottom'">
                        <div class="px-3 px-md-5 py-3 py-md-4 rounded-4 border-start-red box-height-2 effect-2"
                            style="background-color: #F5F5F5;">
                            <p class="fs-1 mb-3 fw-bold" style="color: #FF0000">
                                Brasil: Saturação Real
                            </p>
                            <p class="fs-5 mb-3">
                                O mercado brasileiro enfrenta uma abertura desenfreada de faculdades. Segundo
                                a Demografia Médica (CFM), o Brasil ultrapassará 1 milhão de médicos até 2035,
                                resultando em queda no valor de plantões e insegurança profissional.
                            </p>
                            <p>
                                <small>
                                    Fonte: CFM / Demografia Médica 2024.
                                </small>
                            </p>
                        </div>
                    </div>

                    <div class="col-lg-6" v-reveal="'bottom'">
                        <div class="px-3 px-md-5 py-3 py-md-4 rounded-4 border-start-green box-height-2 effect-2"
                            style="background-color: #F5F5F5;">
                            <p class="fs-1 mb-3 fw-bold" style="color: #06652E">
                                Portugal: Valorização
                            </p>
                            <p class="fs-5 mb-3">
                                O Sistema Nacional de Saúde (SNS) português e o setor privado oferecem remuneração em
                                moeda forte (Euro), qualidade de vida europeia e um reconhecimento institucional que o
                                Brasil perdeu.
                            </p>
                            <p>
                                <small>
                                    Fonte: SNS Portugal / Ordem dos Médicos.
                                </small>
                            </p>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- apresentação dos doutores -->
        <section class="position-relative">
            <div class="container-fluid pt-3 pt-lg-5">
                <div class="row">
                    <div class="col-lg-6 align-self-center px-0 order-lg-2">
                        <div class="p-3">
                            <p class="fs-1 fw-bold mb-4">
                                Dr. Jamil Cade e
                                <br>
                                Dra. Ana Carolina Facundo
                            </p>
                            <p class="fs-5 mb-4">
                                Eles não são apenas tutores; eles são os recordistas. O Dr. Jamil obteve a maior nota da
                                história no processo de revalidação pela Faculdade de Lisboa. A Dra. Ana Carolina traz o
                                rigor acadêmico necessário para vencer a banca examinadora portuguesa.
                            </p>
                            <p class="fs-5 mb-4 text-success fw-semibold">
                                Na CoruJÁ, você não estuda com quem leu o manual, você estuda com quem escreveu o novo
                                padrão de aprovação.
                            </p>
                            <div class="row">
                                <div class="col-auto position-relative z-3" v-reveal="'bottom'">
                                    <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                                        Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-6 align-self-end px-0 order-lg-1">
                        <img :src="JamilAnaAirplane" alt="" class="img-fluid">
                    </div>
                </div>
            </div>
            <svg class="section-divider" width="100%" height="100" viewBox="0 0 100 100" preserveAspectRatio="none"
                xmlns="http://www.w3.org/2000/svg">
                <polygon points="0,0 0,100 100,100" fill="#032612" />
            </svg>
        </section>

        <!-- complementar -->
        <section style="background-color: #032612">
            <div class="container py-3">
                <div class="row">
                    <div class="col-md-6 col-lg-3 mb-3" v-for="i in dadosLista" :key="i.id" v-reveal="'bottom'">
                        <div class="p-3">
                            <p class="text-center fw-bold display-4 mb-0" style="color: #14AE5C">
                                {{ i.title }}
                            </p>
                            <p class="text-center text-light fs-5 fw-light mb-2">
                                {{ i.content }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- por que a corujá é diferente? -->
        <section style="background-color: #032612">
            <div class="container py-5">
                <div class="row mb-4">
                    <div class="col">
                        <h1 class="text-center mb-3 fw-bold text-light" v-reveal="'bottom'">
                            Por que a CoruJÁ é diferente?
                        </h1>
                    </div>
                </div>
                <div class="row mb-4">
                    <div class="col-md-6 mb-4" v-for="i in diferencaLista" :key="i.id" v-reveal="'bottom'">
                        <div class="p-5 bg-white rounded-5 effect-3">
                            <p class="fs-2 text-danger fw-bold text-center mb-3">
                                <font-awesome-icon :icon="i.icon" class="text-danger" />
                                {{ i.title }}
                            </p>
                            <p class="fs-5">
                                {{ i.content }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- depoimentos dos nossos alunos --
        <section style="background-color: #032612">
            <div class="container py-5">
                <div class="row mb-4">
                    <div class="col">
                        <h1 class="fw-bold text-center text-white">
                            Depoimentos de Nossos Alunos
                        </h1>
                    </div>
                </div>
                <div class="row mb-4">
                    <div class="col-lg-9 col-xxl-6 mx-auto">
                        <div class="row">
                            <div class="col-md-6 p-3 mb-3 mb-md-0" role="button"
                                @click="openPlayer('5RAc5SiHPF8mcU3G', 'DR. SÉRGIO CABRAL')" v-reveal="'bottom'">
                                <img :src="SergioCabral" alt="Dr Sérgio Cabral"
                                    class="w-100 border border-white rounded-top-4">
                                <div class="py-3 text-center rounded-bottom-4 border border-white">
                                    <p class="fs-4 fw-semibold mb-0" style="color: #14AE5C">
                                        DR. SÉRGIO CABRAL
                                    </p>
                                    <p class="fs-5 text-white fw-light">
                                        Ginecologista - Aluno CoruJÁ
                                    </p>
                                </div>
                            </div>
                            <div class="col-md-6 p-3" role="button"
                                @click="openPlayer('pIF4TbCOcePiHkGp', 'DRA. MARIA LETÍCIA')" v-reveal="'bottom'">
                                <img :src="MariaLeticia" alt="Dr Sérgio Cabral"
                                    class="w-100 border border-white rounded-top-4">
                                <div class="py-3 text-center rounded-bottom-4 border border-white">
                                    <p class="fs-4 fw-semibold mb-0" style="color: #14AE5C">
                                        DRA. MARIA LETÍCIA
                                    </p>
                                    <p class="fs-5 text-white fw-light">
                                        Médica Validada em Portugal
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>
        !--  -->
        <section style="background-color: #032612" class="py-5">
            <div class="container">
                <h1 class="fw-bold text-center text-white mb-5">Depoimentos de Nossos Alunos</h1>

                <swiper :modules="modules" :slides-per-view="1" :space-between="20" :loop="true"
                    :autoplay="{ delay: 5000 }" :navigation="true" :pagination="{ clickable: true }" :breakpoints="{
                        '768': { slidesPerView: 2 },
                        '1024': { slidesPerView: 3 }
                    }" class="pb-5">
                    <swiper-slide v-for="item in depoimentosList" :key="item.id" v-reveal="'bottom'">
                        <div class="card-depoimento h-100" role="button" @click="openPlayer(item.videoKey, item.name)">
                            <img :src="item.img" :alt="item.name" class="w-100 border border-white rounded-top-4">
                            <div class="py-3 text-center rounded-bottom-4 border border-white bg-transparent">
                                <p class="fs-5 fw-semibold mb-0" style="color: #14AE5C">
                                    {{ item.name }}
                                </p>
                                <p class="small text-white fw-light mb-0">
                                    {{ item.tipo }}
                                </p>
                            </div>
                        </div>
                    </swiper-slide>
                </swiper>

                <div class="row">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                            Quero garantir minha vaga <span class="fw-semibold">com desconto</span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- a preparação mais completa -->
        <section class="py-4 px-2">
            <div class="container my-5 px-3 position-relative rounded-5 border-success border border-3">
                <p class="text-position-1 text-1 text-white mb-0 py-2 px-3 rounded-3"
                    style="background-color: #06652E; letter-spacing: 3px;">
                    A PREPARAÇÃO MAIS COMPLETA
                </p>

                <div class="row pt-5 mb-4">
                    <div class="col pt-3">
                        <h1 class="text-center fw-bold" style="color: #06652E" v-reveal="'bottom'">
                            Combo Completo CoruJÁ 2026
                        </h1>
                    </div>
                </div>

                <div class="row mb-4">
                    <div class="col-auto mx-lg-auto" v-reveal="'bottom'">
                        <ul class="list-unstyled">
                            <li class="mb-3 fs-4 d-flex align-items-center gap-2">
                                <img :src="CheckIcon2" alt="" width="40">
                                Curso de revisão &euro; 290,00
                            </li>
                            <li class="mb-3 fs-4 d-flex align-items-center gap-2">
                                <img :src="CheckIcon2" alt="" width="40">
                                Manual completo &euro; 149,00
                            </li>
                            <li class="mb-3 fs-4 d-flex align-items-center gap-2">
                                <img :src="CheckIcon2" alt="" width="40">
                                Mentoria &euro; 988,90
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="row mb-4">
                    <div class="col-md-auto mx-auto rounded-4" style="background-color: #032612" v-reveal="'bottom'">
                        <div class="p-4">
                            <p class="text-center text-light fs-3">
                                De &euro; 1428,80 por
                            </p>
                            <p class="text-center display-1 fw-bold" style="color: #14AE5C">
                                <small><sup>&euro;</sup></small>
                                1.048
                                <small><sup>,42</sup></small>
                            </p>
                            <p class="text-warning text-center">
                                Economia de &euro;380 garantindo o Combo agora
                            </p>
                        </div>
                    </div>
                </div>

                <div class="row mb-4">
                    <div class="col-auto mx-auto" v-reveal="'bottom'">
                        <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                            QUERO GARANTIR MINHA APROVAÇÃO
                        </button>
                    </div>
                </div>

                <div class="row">
                    <div class="col-lg-auto mx-auto" v-reveal="'bottom'">
                        <p class="text-secondary">
                            <img :src="Guarantee" alt="" width="30"> Garantia de 7 dias
                            &nbsp;&nbsp;&nbsp;&nbsp;
                            <img :src="Lock" alt="" width="30"> Pagamento Seguro
                        </p>
                    </div>
                </div>
            </div>
            <div class="container">
                <div class="row mb-3">
                    <div class="col-md-4 ps-md-0 mb-3">
                        <div class="rounded-5 border border-success border-3 p-4" v-reveal="'bottom'">
                            <p class="text-center fs-3 text-success fw-semibold">
                                Mentoria 1ª Fase
                            </p>
                            <p class="fs-1 fw-bold text-success text-center">
                                &euro; 988,90
                            </p>
                            <p class="text-center fs-5">
                                Inscrição Individual
                            </p>
                            <div class="row mb-3">
                                <div class="col-auto mx-auto" v-reveal="'bottom'">
                                    <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                                        Comprar Mentoria
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 px-md-0 mb-3">
                        <div class="rounded-5 border border-success border-3 p-4" v-reveal="'bottom'">
                            <p class="text-center fs-3 text-success fw-semibold">
                                Curso de Revisão
                            </p>
                            <p class="fs-1 fw-bold text-success text-center">
                                &euro; 290,00
                            </p>
                            <p class="text-center fs-5">
                                Inscrição Individual
                            </p>
                            <div class="row mb-3">
                                <div class="col-auto mx-auto" v-reveal="'bottom'">
                                    <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                                        Comprar Revisão
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 pe-md-0 mb-3">
                        <div class="rounded-5 border border-success border-3 p-4" v-reveal="'bottom'">
                            <p class="text-center fs-3 text-success fw-semibold">
                                Manual Completo
                            </p>
                            <p class="fs-1 fw-bold text-success text-center">
                                &euro; 149,90
                            </p>
                            <p class="text-center fs-5">
                                Inscrição Individual
                            </p>
                            <div class="row mb-3">
                                <div class="col-auto mx-auto" v-reveal="'bottom'">
                                    <button class="btn btn-danger py-3 px-5 btn-lg effect-3">
                                        Comprar Manual
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- dúvidas frequentes -->
        <section>
            <div class="container py-5">
                <div class="row mb-4">
                    <div class="col">
                        <h1 class="text-center mb-3 fw-bold" v-reveal="'bottom'">
                            Dúvidas Frequentes
                        </h1>
                    </div>
                </div>
                <div class="row">
                    <div class="col-lg-9 mx-auto">
                        <div class="accordion accordion-flush" id="accordionListFAQ">
                            <div v-for="(item, index) in faqItems" :key="index"
                                class="accordion-item mb-4 rounded-3 bg-light shadow" v-reveal="'bottom'">
                                <h2 class="accordion-header">
                                    <button class="accordion-button collapsed rounded-3 fs-5 bg-light" type="button"
                                        data-bs-toggle="collapse" :data-bs-target="'#flush-collapse' + index"
                                        aria-expanded="false" :aria-controls="'flush-collapse' + index">
                                        {{ item.pergunta }}
                                    </button>
                                </h2>
                                <div :id="'flush-collapse' + index" class="accordion-collapse collapse"
                                    data-bs-parent="#accordionListFAQ">
                                    <div class="accordion-body">
                                        {{ item.resposta }}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Modal -->
        <dialog ref="modalVideo" class="custom-modal">
            <div class="modal-content-wrapper">
                <div class="modal-header-custom">
                    <h2 class="fw-semibold">{{ currentDoctorName }}</h2>
                    <button type="button" class="btn-close-custom" @click="closeModal">&times;</button>
                </div>

                <div class="modal-body">
                    <iframe v-if="currentPlayerUrl" id="player" :src="currentPlayerUrl" frameborder="0"
                        class="d-block mx-auto" style="aspect-ratio: 16 / 9; width: 100%;" allowfullscreen></iframe>
                </div>

                <div class="text-end mt-3">
                    <button type="button" class="btn btn-light" @click="closeModal">Fechar</button>
                </div>
            </div>
        </dialog>
    </main>
    <footer>
        <div class="container-fluid py-3">
            <div class="row justify-content-between">
                <div class="col-md-auto align-self-center p-md-5 mb-3 mb-md-0">
                    <img :src="BlackLogo" height="100" alt="logo corujá">
                </div>
                <div class="col-md-auto align-self-center">
                    <p class="text-center p-md-5 fs-5">
                        &copy; 2026 CoruJÁ Mentoria. Todos os direitos reservados.
                    </p>
                </div>
            </div>
        </div>
    </footer>
</template>

<style scoped>
.section-divider {
    display: block;
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    z-index: 2;
}

.border-start-red {
    border-left: solid 24px #FF0000;
}

.border-start-green {
    border-left: solid 24px #06652E;
}

.text-position-1 {
    position: absolute;
    top: -20px;
    left: 50%;
    transform: translateX(-50%);
}

.text-1 {
    font-size: clamp(12px, 2vw, 24px);
    min-width: 290px;
    text-align: center;
}

#hero {
    background-image: url(../assets/img/hero.png);
    background-position: center left;
    background-repeat: no-repeat;
    background-size: cover;
    min-height: 600px;
}

.box-height-1 {
    min-height: 240px;
}

.box-height-2 {
    min-height: 300px;
}

@media screen and (min-width: 612px) {
    .text-position-1 {
        top: -20px;
    }

    .text-1 {
        min-width: 370px;
    }
}

@media screen and (min-width: 883px) {
    .text-1 {
        min-width: 400px;
    }
}

@media screen and (min-width: 768px) {
    .box-height-1 {
        min-height: 270px;
    }

    .box-height-2 {
        min-height: 290px;
    }
}

@media screen and (min-width: 992px) {
    .box-height-2 {
        min-height: 440px;
    }
}

@media screen and (min-width: 1200px) {
    #hero {
        min-height: 88dvh;
    }

    .box-height-1 {
        min-height: 240px;
    }

    .box-height-2 {
        min-height: 360px;
    }
}

@media screen and (min-width: 1400px) {
    .box-height-2 {
        min-height: 330px;
    }
}
</style>