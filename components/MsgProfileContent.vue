<script setup>

  const props = defineProps({
    profile: {
        type: Object,
        required: false
    }
  })

  const show = ref(false);

  // TODO:ダミーの画像なので後で消去
  const array = [
    'https://media.gettyimages.com/id/1383493764/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E7%AC%91%E9%A1%94%E3%81%AE%E8%8B%A5%E3%81%84%E3%82%A2%E3%82%B8%E3%82%A2%E4%BA%BA%E7%94%B7%E6%80%A7%E3%81%AE%E8%82%96%E5%83%8F.jpg?s=1024x1024&w=gi&k=20&c=7_tru54N_qifjtSS3kiloZK1YeX671bwUQXLTe6gtQo=',
    'https://media.gettyimages.com/id/1328998043/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E3%82%A2%E3%82%B8%E3%82%A2%E3%81%AE%E8%8B%A5%E6%89%8B%E7%94%B7%E6%80%A7%E3%81%AE%E8%82%96%E5%83%8F.jpg?s=1024x1024&w=gi&k=20&c=IDM-4NYKuFQ08ZXoaXwj4F8mj1rpF-vIdF2B5QIKg-E=',
    'https://media.gettyimages.com/id/1328709540/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E3%83%87%E3%82%B8%E3%82%BF%E3%83%AB%E3%82%BF%E3%83%96%E3%83%AC%E3%83%83%E3%83%88%E3%82%92%E6%8C%81%E3%81%A4%E8%8B%A5%E3%81%84%E3%82%A2%E3%82%B8%E3%82%A2%E3%81%AE%E5%A5%B3%E6%80%A7.jpg?s=1024x1024&w=gi&k=20&c=_NxVZuZZpQJBYQKBPZvuH5CqEXVVuF3XBWIolIY72BE=',
    'https://media.gettyimages.com/id/1035439062/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/japanese-portrait-of-a-young-man.jpg?s=1024x1024&w=gi&k=20&c=M20PrNZGHrRlOAJyCctIsyMLf7w75vz9HRIolFbDFZQ=',
    'https://media.gettyimages.com/id/1330249650/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E3%83%A9%E3%83%83%E3%83%97%E3%83%88%E3%83%83%E3%83%97%E3%82%92%E6%8C%81%E3%81%A4%E8%8B%A5%E3%81%84%E3%82%A2%E3%82%B8%E3%82%A2%E4%BA%BA%E7%94%B7%E6%80%A7%E3%81%AE%E8%82%96%E5%83%8F.jpg?s=1024x1024&w=gi&k=20&c=bm8oYQYczA74rC8pWTZOJ1b-pxuTYoxX0Lsd0BmGi_4=',
    'https://media.gettyimages.com/id/1363985196/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E9%9B%BB%E8%A9%B1%E3%81%A7%E8%A9%B1%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%82%A2%E3%82%B8%E3%82%A2%E4%BA%BA%E7%94%B7%E6%80%A7.jpg?s=1024x1024&w=gi&k=20&c=qHb5pym6orQREnamZp0QrMu3ArA2rzbDlxB2axWlGNQ=',
    'https://media.gettyimages.com/id/1385925142/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E5%9B%B3%E6%9B%B8%E9%A4%A8%E3%81%A7%E9%81%B8%E6%8A%9C%E5%9B%B3%E6%9B%B8%E3%82%92%E9%96%8B%E5%82%AC%E4%B8%AD%E3%81%AE%E3%82%A2%E3%82%B8%E3%82%A2%E5%A5%B3%E5%AD%90%E5%AD%A6%E7%94%9F.jpg?s=1024x1024&w=gi&k=20&c=MLWTKeKNhY4V_Uv1iwm97wSEXB55Z6oBFO6rq3pgA9A=',
    'https://media.gettyimages.com/id/1418546174/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E6%95%99%E5%AE%A4%E3%82%84%E4%B8%AD%E5%B0%8F%E4%BC%81%E6%A5%AD%E3%81%A7%E3%83%A9%E3%83%83%E3%83%97%E3%83%88%E3%83%83%E3%83%97%E3%82%92%E6%8C%81%E3%81%A4%E8%8B%A5%E3%81%84%E7%94%B7%E6%80%A7%E3%81%AE%E3%83%9D%E3%83%BC%E3%83%88%E3%83%AC%E3%83%BC%E3%83%88.jpg?s=1024x1024&w=gi&k=20&c=pfJ5OIOz_cCXygaqqhJAk-0XbUlzrfJ_KusPuYOQhQ8=',
    'https://media.gettyimages.com/id/1363985150/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E3%82%A2%E3%82%B8%E3%82%A2%E4%BA%BA%E3%81%AE%E8%82%96%E5%83%8F.jpg?s=1024x1024&w=gi&k=20&c=nz8U_Qt2Se6h2Z0nZlvONNl338NvSFoESjMXG-7BbCE=',
    'https://media.gettyimages.com/id/927775484/ja/%E3%82%B9%E3%83%88%E3%83%83%E3%82%AF%E3%83%95%E3%82%A9%E3%83%88/%E5%AD%A6%E7%94%9F%E3%81%AB%E3%83%9B%E3%83%AF%E3%82%A4%E3%83%88%E3%83%9C%E3%83%BC%E3%83%89%E3%81%AB%E4%BD%9C%E6%88%90.jpg?s=1024x1024&w=gi&k=20&c=7UqnvuYvgH3Q3QsSo8dHRyS__EwWGPOmfRo5jRisKmI='

  ];
  // ランダムなインデックスを生成
  const randomIndex = Math.floor(Math.random() * array.length);
  // ランダムな要素を選択
  const randomElement = array[randomIndex];

  console.log(randomElement);

</script>
<template>
  <v-card
    :loading="loading"
    class="mx-auto my-3"
    max-width="300"
    height="480px"
  >
    <template v-slot:loader="{ isActive }">
      <!-- <v-progress-linear
        :active="isActive"
        color="deep-purple"
        height="4"
        indeterminate
      ></v-progress-linear> -->
    </template>

    <!-- <v-img
      height="40%"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
      cover
    > -->
    <v-row align-content="center" style="">
      <v-col align="center">
            <v-avatar
              class="mx-auto"
              color="grey"
              rounded="100"
              size="80"
            >
          <v-img :src="randomElement" cover></v-img>
        </v-avatar>
      </v-col>
    </v-row>
      <!-- <v-avatar
        class="mx-auto"
        color="grey"
        rounded="100"
        size="100"
      >
        <v-img src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg" cover></v-img>
      </v-avatar> -->
    <!-- </v-img> -->
    <v-card-item>
      <v-card-title>{{ profile.name }}</v-card-title>
      <v-card-subtitle>
        <span class="me-1">{{ profile.belongings }}</span>
        <v-icon
          color="error"
          icon="mdi-fire-circle"
          size="small"
        ></v-icon>
      </v-card-subtitle>
    </v-card-item>
    <v-card-text>
      <v-chip-group
        v-model="selection"
        active-class="deep-purple white--text"
        column
      >
        <v-chip>UI・UX</v-chip>

        <v-chip>SaaS</v-chip>

        <v-chip>人材業界</v-chip>

        <v-chip>東京大学</v-chip>
      </v-chip-group>
    </v-card-text>
    <v-card-text>
      
      <v-row
        align="center"
        class="mx-0"
      >

        <!-- <v-rating
          :model-value="4.5"
          color="amber"
          density="compact"
          size="small"
          half-increments
          readonly
        ></v-rating> -->

        <!-- <div class="text-grey ms-4">
          4.5 (413)
        </div> -->
      </v-row>

      <div class="my-4 text-subtitle-1">
      </div>

      <div>{{ profile.strength }}</div>
    </v-card-text>
    <v-row align-content="center" class="mb-3">
      <v-col align="center">
        <v-btn rounded="xl" color="primary" elevated>メッセージを送る</v-btn>
      </v-col>
    </v-row>
    <v-divider class="mx-4 mb-1" ></v-divider>
  </v-card>
</template>
