<template>
  <div class="container">
    <div class="container-personal">
      <!-- Title and Subtitle -->
      <div class="container-personal__text-block">
        <h1 class="heading-primary">
          <span class="heading-primary--main">Álvaro Saavedra Díaz</span>
          <span class="heading-primary--sub">Software Developer</span>
        </h1>
      </div>

      <!-- Card and Little Bio -->
      <div class="container-personal__card-bio">
        <a-row type="flex" justify="center">
          <!-- Card -->
          <a-col :span="6">
            <a-card hoverable>
              <img
                slot="cover"
                alt="Álvaro Saavedra"
                src="https://scontent-mad1-1.cdninstagram.com/v/t51.2885-15/e35/p1080x1080/82707403_210277496805111_3521147832403782819_n.jpg?_nc_ht=scontent-mad1-1.cdninstagram.com&_nc_cat=103&_nc_ohc=G-a8ezN7S-IAX-ERMTN&oh=3ddd3c93540954402e89e4ce653321fe&oe=5F2CBA21"
              />

              <template slot="actions" class="ant-card-actions">
                <a href="https://github.com/alvarooncode" target="_blank" rel="noopener noreferrer">
                  <a-icon key="github" type="github" />
                </a>
                <a
                  href="https://www.linkedin.com/in/alvarojosesaavedradiaz/"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <a-icon key="linkedin" type="linkedin" />
                </a>
                <a
                  href="https://twitter.com/alvarooncode"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <a-icon key="twitter" type="twitter" />
                </a>
              </template>
            </a-card>
          </a-col>

          <!-- Bio -->
          <a-col :span="8">
            <h3 class="heading-tertiary card-bio__bio">Hello, World!</h3>
            <p
              class="paragraph card-bio__bio"
            >I am a Software Developer, based in Seville (Spain). Currently, I work on International Business Development and Projects Department at Emergya, as Full Stack JavaScript Developer. We migrate old-fashioned websites to newer technologies for international brands, all over the world.</p>
            <p class="paragraph card-bio__bio">JavaScript friends are welcome here!</p>
          </a-col>
        </a-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>
