<template>
  <div :class="$style.Advisory">
    <div :class="$style.AdvisoryContainer">
      <div :class="$style.AdvisoryContents">
        <div>
          <span :class="$style.AdvisoryContentsTitle">{{
            $t('新型コロナ受診相談窓口（日本語のみ）')
          }}</span>
        </div>
        <div :class="[$style.AdvisoryContentsColsSentense, 'mt-4']">
          {{ $t('帰国者・接触者相談センター（保健所）') }}
        </div>
        <div :class="[$style.AdvisoryBoxContainer, $style.AdvisoryWhiteBox]">
          <span :class="$style.AdvisoryWhiteBoxSentense">
            {{ $t('24時間対応') }}
          </span>
        </div>
        <div
          :class="[$style.AdvisoryLink, $style.AdvisoryBlockCentering, 'mt-4']"
        >
          <a :href="getUrl" target="_blank" rel="noopener noreferrer">
            <span>{{
              $t('各保健所の電話番号は新型コロナウイルス感染症ポータルページへ')
            }}</span>
            <v-icon size="18">
              mdi-open-in-new
            </v-icon>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Status from '@/components/flow/status.json'
export default {
  data() {
    return {
      status: Status
    }
  },
  computed: {
    getUrl() {
      let URL = this.status.infoURL
      if (URL.length === 0) {
        URL = 'https://www.pref.fukuoka.lg.jp/contents/covid-19-portal.html'
      }
      return URL
    }
  }
}
</script>

<style module lang="scss">
.Advisory {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  color: $gray-2;

  &Container {
    background-color: $gray-5;
    border-radius: 4px;
    height: 100%;
    padding: 30px 20px 20px 20px;
    margin-bottom: 10px;
    text-align: center;
  }

  &Contents {
    font-weight: bold;

    &:not(:first-child) {
      border-top: 0.5px solid $gray-4;
    }

    &Title {
      font-size: 26px;
      line-height: 28px;
    }

    &Title2 {
      font-size: 18px;
    }

    &SubTitle {
      font-size: 18px;
    }

    &ColsSentense {
      line-height: 18px;
    }
  }

  &BlockCentering {
    display: flex;
    justify-content: center;
  }

  &Link {
    line-height: 22px;
    text-align: left;

    a {
      color: rgba(0, 0, 0, 0.87) !important;
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }

  &TelephoneArea {
    display: inline-flex;
  }

  &Telephone {
    display: flex;
    align-items: center;
    font-size: 27px;
    font-weight: bold;

    &:link,
    &:visited,
    &:hover,
    &:active,
    &:focus {
      color: inherit;
      text-decoration: none;
      @media screen {
        // printだとoutlineが太くなってしまい読みにくいので、消す処理
        outline: 1px dotted $gray-3;
      }
    }

    &Icon {
      display: inline-block;
      margin-right: 5px;
      width: 26px;
      height: 26px;
    }
  }

  &BoxContainer {
    border-radius: 4px;
    text-align: center;
    padding: 20px 10px;
    margin: 24px auto;
  }

  &WhiteBox {
    background-color: $white;
    max-width: 160px;
    padding: 10px;

    &Sentense {
      color: $blue-1;
      font-size: 18px;
      font-weight: bold;
    }
  }
}
</style>
