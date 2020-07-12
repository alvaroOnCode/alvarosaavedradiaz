<template>
  <div class="container">
    <div class="container-personal">
      <!-- Title and Subtitle -->
      <a-row class="container-personal__text-block" type="flex" justify="center">
        <a-col :span="16">
          <h1 class="heading-primary">
            <span class="heading-primary--main">Álvaro Saavedra Díaz</span>
            <span class="heading-primary--sub">Software Developer</span>
          </h1>
        </a-col>
      </a-row>

      <!-- Card and Little Bio -->
      <a-row class="container-personal__card-bio" type="flex" justify="center">
        <!-- Card -->
        <a-col :span="6">
          <a-card hoverable>
            <img
              slot="cover"
              alt="Álvaro Saavedra"
              src="https://scontent-mad1-1.cdninstagram.com/v/t51.2885-15/e35/p1080x1080/82707403_210277496805111_3521147832403782819_n.jpg?_nc_ht=scontent-mad1-1.cdninstagram.com&_nc_cat=103&_nc_ohc=G-a8ezN7S-IAX-ERMTN&oh=3ddd3c93540954402e89e4ce653321fe&oe=5F2CBA21"
            />

            <template slot="actions" class="ant-card-actions">
              <SocialMedia />
            </template>
          </a-card>
        </a-col>

        <!-- Bio -->
        <a-col :span="8">
          <h3 class="heading-tertiary card-bio__bio">¡Hola, Mundo!</h3>
          <p
            class="paragraph card-bio__bio"
          >Soy desarrollador de software y vivo en Sevilla (España). Actualmente trabajo como Full-Stack JavaScript Developer en la divión internacional de Emergya Consultoría. Allí, ayudo a migrar portales que fueron desarrollados con tecnologías que hoy consideramos obsoletas a stacks más actuales.</p>

          <p class="paragraph card-bio__bio">
            Hace algunos años que me adentré en el universo de
            <u>JavaScript</u> y no salgo de mi asombro al ver la cantidad de cosas que se pueden hacer con un único lenguaje. En este blog escribiré mayoritariamente sobre
            <u>JavaScript</u> y su ecosistema.
          </p>

          <p class="paragraph card-bio__bio">
            Me apasiona programar, pero siempre he tenido debilidad y admiración por la arquitectura. Dedico parte de mi tiempo libre a leer, dibujar y desarrollar experiencias arquitectónicas interactivas (archviz) con
            <u>Unity</u> y
            <u>Unreal</u>. Esta pasión me ayudó a abrir los ojos y aprender a mirar y a admirar... y es por eso, supongo, por lo que descubrí la fotografía.
          </p>

          <p class="paragraph card-bio__bio">Ya sabes un poco más sobre mí, ¿hablamos?</p>
        </a-col>
      </a-row>
    </div>
  </div>
</template>
