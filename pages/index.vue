<template>
  <div class="container">
    <div class="container-personal">
      <!-- Title and Subtitle -->
      <a-row class="container-personal__text-block" type="flex" justify="center">
        <a-col>
          <h1 class="heading-primary">
            <span class="heading-primary--main">Álvaro Saavedra Díaz</span>
            <span class="heading-primary--sub">Software Developer</span>
          </h1>
        </a-col>
      </a-row>

      <!-- Card and Little Bio -->
      <a-row class="container-personal__card-bio" type="flex" justify="space-between">
        <!-- Card -->
        <a-col :span="8" class="col__card-bio--card">
          <a-card hoverable>
            <img
              slot="cover"
              alt="Álvaro Saavedra"
              src="https://res.cloudinary.com/alvarooncode/image/upload/v1597597284/alvarosaavedradiaz/assets/images/alvarosaavedra-profile_st1emv.jpg"
            />

            <template slot="actions" class="ant-card-actions">
              <SocialMedia />
            </template>
          </a-card>
        </a-col>

        <!-- Bio -->
        <a-col :span="15" class="col__card-bio--bio">
          <h3 class="heading-tertiary card-bio__bio">¡Hola, Mundo!</h3>
          <p class="paragraph card-bio__bio">
            Soy desarrollador de software y vivo en Sevilla (España).
            Actualmente trabajo como Full-Stack JavaScript Developer en la
            divión internacional de Emergya Consultoría. Allí, ayudo a migrar
            portales que fueron desarrollados con tecnologías que hoy
            consideramos obsoletas a stacks más actuales.
          </p>

          <p class="paragraph card-bio__bio">
            Hace algunos años que me adentré en el universo de
            <u>JavaScript</u> y no salgo de mi asombro al ver la cantidad de
            cosas que se pueden hacer con un único lenguaje. En este blog
            escribiré mayoritariamente sobre
            <u>JavaScript</u> y su ecosistema.
          </p>

          <p class="paragraph card-bio__bio">
            Me apasiona programar, pero siempre he tenido debilidad y admiración
            por la arquitectura. Dedico parte de mi tiempo libre a leer, dibujar
            y desarrollar experiencias arquitectónicas interactivas (archviz)
            con
            <u>Unity</u> y
            <u>Unreal</u>. Esta pasión me ayudó a abrir los ojos
            y aprender a mirar y a admirar... y es por eso, supongo, por lo que
            descubrí la fotografía.
          </p>

          <p class="paragraph card-bio__bio">Ya sabes un poco más sobre mí, ¿hablamos?</p>
        </a-col>
      </a-row>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Álvaro Saavedra Díaz 🧑‍💻 Software Developer",
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content:
            "Página web de Álvaro Saavedra (@alvaroOnCode), donde encontrarás información personal, profesional y artículos de desarrollo de software.",
        },
      ],
    };
  },
};
</script>
