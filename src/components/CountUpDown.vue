  <template>
    <v-app-bar color="primary">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-app-bar-title>
        SamplePage
      </v-app-bar-title>
      <!--v-btn>SignIn</v-btn-->
      <v-btn icon="mdi-home" class="ma-2" to="/"></v-btn>
    </v-app-bar>
    <v-container>
      <!--v-system-bar color="secondary">
        System Bar
      </v-system-bar-->
      <h1>{{ msg }}</h1>
      <p>ボタン１</p>
      <v-btn @click="countUp">Test</v-btn>
      <hr/>
      <p>ボタン２</p>
      <v-btn @click="countUp" color="blue">Test</v-btn>
      <hr/>
      <p>ボタン３</p>
      <v-btn @click="countDown" color="primary">Test</v-btn>
      <hr/>
      <p>ボタン４</p>
      <v-btn @click="countDown" outlined color="blue">Test</v-btn>
      <hr/>
      <p>ボタン５</p>
      <v-btn class="ma-2" to="/">Homeに戻る</v-btn>
      <hr/>
      <p>テキストフィールド</p>
      <v-sheet width="80%">
        <v-text-field label="入力できます" variant="outlined" placeholder="文字数を表示する（数えるだけ）" counter="20" clearable></v-text-field>
      </v-sheet>
      <hr/>
      <p>プルダウンメニュー</p>
      <v-select label="選択できます" :items="['本社','西','足立','葛飾']" class="ma-2" v-model="select"></v-select>
      <hr/>
      <p>スライダー</p>
      <v-slider v-model="slideval" color="black" label="カウント" :min="0" :max="100" :step="1" thumb-label></v-slider>
      <h1>{{ slideval }}</h1>
      <hr/>
      <p>ラジオボタン</p>
      <div class="d-flex justify-center" >
        <div>
          <v-radio-group v-model="radioGroup">
            <div class="d-flex flex-row" >
              <v-radio label="Hoge1" value="1"></v-radio>
              <v-radio label="Hoge2" value="2"></v-radio>
              <v-radio label="Hoge3" value="3"></v-radio>
            </div>
          </v-radio-group>  
        </div> 
      </div>
      <h1>{{ radioGroup }}</h1>
      <hr/>
      <p>チェックボックス</p>
      <v-row>
      <v-col>
        <v-checkbox v-model="selected" value="1" label="Hoge1">
        </v-checkbox>
      </v-col>
      <v-col>
        <v-checkbox v-model="selected" value="2" label="Hoge2" color="red">
        </v-checkbox>
      </v-col>
      <v-col>
        <v-checkbox v-model="selected" value="3" label="Hoge3" color="blue">
        </v-checkbox>
      </v-col>
      </v-row>
      <h1>{{selected}}</h1>
      <hr/>
        <p>ダイアログ</p>
        <v-btn color="primary">
          Open Dialog
          <v-dialog v-model="dialog" activator="parent" >
            <v-sheet>
              <v-sheet class="my-2 mx-5">
                <h2>Dialog!</h2>
                <p class="my-4">
                  これはダイアログです
                </p>
                <v-btn color="primary" block @click="dialog = false">Close</v-btn>
              </v-sheet>
            </v-sheet>
          </v-dialog>
        </v-btn>
      <hr/>
      <p>選択リスト</p>
      <v-list @click:select="clickItem">
      <v-list-item value="1">
        <v-list-item-title>HOGE1</v-list-item-title>
        </v-list-item>
      <v-list-item value="2">
        <v-list-item-title>HOGE2</v-list-item-title>
        </v-list-item>
      <v-list-item value="3">
        <v-list-item-title>HOGE3</v-list-item-title>
        </v-list-item>
      </v-list>
      <h1>{{ message }}</h1>
      <hr/>
      <p>データテーブル</p>
      <v-data-table
        v-model:items-per-page="itemsPerPage"
        :headers="headers"
        :items="dataset"
        item-value="name"
        class="elevation-1"
      ></v-data-table>
    </v-container>
  </template>
  
  <script>
  import { VDataTable } from 'vuetify/lib/labs/components.mjs';

  export default {
    name: "CountUpDown",

    props: {
      msg: String
    },

    data () {
      return {
        count: 0,
        message: "",
        select: null,
        selected: [],
        slideval: 0,
        radioGroup: "3",
        dialog: false,
        itemsPerPage: 5,

        headers: [
          {
            title: '都道府県',
            align: 'start',
            sortable: false,
            key: 'name',
          },
          { title: 'no', align: 'end', key: 'no' },
          { title: '面積', align: 'end', key: 'area' },
        ],

        dataset: [
          {name: '北海道', no: 1,  area: 83456.20 },
          {name: '長野県', no: 2,  area: 13562.23 },
          {name: '東京都', no: 3,  area: 2187.42 },
          {name: '和歌山県', no: 4,area: 4726.12 },
          {name: '香川県', no: 5,  area: 1876.47 },
          {name: '神奈川県', no: 6,area: 2415.84 },
          {name: '岡山県', no: 7,  area: 7113.00 },
          {name: '鹿児島県', no: 8,area: 9187.80 },
          {name: '宮城県', no: 9,  area: 7285.73 },
          {name: '石川県', no: 10, area: 4185.47 },                                
        ],
      }
    },

    components: {
      VDataTable,
    },

    methods: {
      countUp(){
        this.count++;
      },
      countDown(){
        this.count--;
      },
      touchStart(e){
        e.target.classList.add('touched');
      },
      touchEnd(e){
        e.target.classList.remove('touched');
      },
      clickItem(arg){
      this.message = arg.id;
      }
    },
  
  };
  </script>
  
  <style>
  hr {
		height:0px;
		margin:0 0 10px 0;
		border-color:#cccccc;
		border-style:solid;
		border-width:0 0 1px 0;
		padding:0 0 10px 0;
	}
  </style>