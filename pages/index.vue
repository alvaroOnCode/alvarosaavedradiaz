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
          <h3 class="heading-tertiary card-bio__bio">Hello, World!</h3>
          <p
            class="paragraph card-bio__bio"
          >I am a Software Developer, based in Seville (Spain). Currently, I work as Full Stack JavaScript Developer on International Business Development and Projects Department at Emergya migrating old-fashioned websites to newer technologies.</p>
          <p
            class="paragraph card-bio__bio"
          >I love programming, but I’ve always had a soft spot for Architecture. I dedicate time to reading, sketching and creating interactive archviz (architectural visualizations) and renders. But mostly, I open my eyes and look, and admire... and that, I guess, is the reason I discovered photography.</p>
          <p class="paragraph card-bio__bio">Now you know a bit about me. Let's talk!</p>
        </a-col>
      </a-row>
    </div>
  </div>
</template>
