<script>
import html2canvas from 'html2canvas';

export default {
    name: "App",
    data() {
        return {
            imageData: null,
            newData: null
        }
    },
    mounted() {
        this.exportPdf();
    },
    methods: {
        exportPdf() {
            html2canvas(this.$refs.pdf).then(canva => {
                this.imageData = canva.toDataURL("image/jpg");
                this.newData = this.imageData.replace(/^data:image\/jpg/, "data:application/octet-stream");
            });
        }
    }
}
</script>

<template>
    <div ref="pdf">
        <a href="https://vitejs.dev" target="_blank">
            <img src="/vite.svg" class="logo" alt="Vite logo"/>
        </a>
        <a href="https://vuejs.org/" target="_blank">
            <img src="./assets/vue.svg" class="logo vue" alt="Vue logo"/>
        </a>
        <p>Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos de texto. Lorem Ipsum ha sido el
            texto de relleno estándar de las industrias desde el año 1500, cuando un impresor (N. del T. persona que se
            dedica a la imprenta) desconocido usó una galería de textos y los mezcló de tal manera que logró hacer un
            libro de textos especimen. No sólo sobrevivió 500 años, sino que tambien ingresó como texto de relleno en
            documentos electrónicos, quedando esencialmente igual al original. Fue popularizado en los 60s con la
            creación de las hojas "Letraset", las cuales contenian pasajes de Lorem Ipsum, y más recientemente con
            software de autoedición, como por ejemplo Aldus PageMaker, el cual incluye versiones de Lorem Ipsum.</p>
    </div>
    <a :href="newData" download="image.jpg">export pdf</a>
</template>

<style scoped>
.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
}

.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
