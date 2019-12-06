<template>
  <div class="home">

    <div style="padding: 16px">
      <button @click="diffType = 'deep-diff'">Deep diff npm package</button>
      <button @click="diffType = 'deep-object-diff'">Deep object diff npm package</button>
    </div>

    <div v-if="diffType === 'deep-diff'">
      <h1>Deep diff</h1>
      <a href="https://www.npmjs.com/packnumber/deep-diff">npmjs.com/deep-diff</a>
    </div>

    <div v-if="diffType === 'deep-object-diff'">
      <h1>Deep object diff</h1>
      <a href="https://www.npmjs.com/package/deep-object-diff">npmjs.com/deep-object-diff</a>
    </div>

    <div style="padding: 16px">
      <button @click="setPerson1Data()">Fill Person 1</button>
      <button @click="setPerson2Data()">Fill Person 2</button>
      <button @click="setData()">Fill both</button>
      |
      <button @click="clearPerson1Data()">Clear Person 1</button>
      <button @click="clearPerson2Data()">Clear Person 2</button>
      <button @click="clearData()">Clear both</button>
    </div>

    <div class="flex" style="margin-top: 32px">
      <div class="flex">
        <div style="width: 50%; padding: 16px; background-color: rgba(0,0,0,0.05)">
          <form action>
            <div class="field">
              <label for>Nome</label>
              <input type="text" v-model="person1.name" />
            </div>
            <div class="field">
              <label for>Número</label>
              <input type="number" v-model="person1.number" />
            </div>
            <div class="field">
              <label for>Data de nascimento</label>
              <input type="date" v-model="birth" @change="setBirthdate('person1')"/>
            </div>
            <div class="divisor">
              <h2>Lista de amigos</h2>
              <div class="group" v-for="friend in person1.friends">
                <div class="field">
                <label for>Nome do amigo</label>
                <input type="text" v-model="friend.name" />
                <!-- {{ person1.friends }} -->
              </div>
              <div class="field">
                <label for>Idade do amigo</label>
                <input type="text" v-model="friend.age" />
                <!-- {{ person1.friends }} -->
              </div>
              </div>
              <button type="button" @click="addFriend('person1')">adicionar amigo</button>
            </div>
            <div class="divisor">
              <h2>Jogos que já jogou</h2>
              <div class="group" v-for="game in person1.player.games">
                <div class="field">
                  <label for>Nome do jogo</label>
                  <input type="text" v-model="game.name" />
                </div>
              </div>
              <button type="button" @click="addGame('person1')">adicionar jogo já jogado</button>
            </div>
            <div class="divisor">
              <h2>Consoles bonitos</h2>
              <div class="group" v-for="cons in person1.player.consoles">
                <div class="field" >
                  <select name="" id="" v-model="cons.name">
                    <option value="">Selecione um console</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Xbox 360">Xbox 360</option>
                    <option value="Xbox One">Xbox One</option>
                    <option value="Xbox One X">Xbox One X</option>
                    <option value="PS1">PS1</option>
                    <option value="PS2">PS2</option>
                    <option value="PS3">PS3</option>
                    <option value="PS4">PS4</option>
                    <option value="Nintendo Switch">Nintendo Switch</option>
                    <option value="Nintendo 64">Nintendo 64</option>
                  </select>
                </div>
              </div>
              <button type="button" @click="addConsole('person1')">adicionar console</button>
            </div>
          </form>
        </div>

        <div style="width: 50%; padding: 16px; background-color: rgba(0,0,0,0.05)">
          <code>
            <pre>
  {{ person1 }}
            </pre>
          </code>
        </div>
      </div>

      <div class="flex">
        <div style="width: 50%; padding: 16px; background-color: rgba(0,255,0,0.12)">
          <form action>
            <div class="field">
              <label for>Nome</label>
              <input type="text" v-model="person2.name" />
            </div>
            <div class="field">
              <label for>Número</label>
              <input type="number" v-model="person2.number" />
            </div>
            <div class="field">
              <label for>Data de nascimento</label>
              <input type="date" v-model="birth" @change="setBirthdate('person2')"/>
            </div>
            <div class="divisor">
              <h2>Lista de amigos</h2>
              <div class="group" v-for="friend in person2.friends">
                <div class="field">
                <label for>Nome do amigo</label>
                <input type="text" v-model="friend.name" />
                <!-- {{ person2.friends }} -->
              </div>
              <div class="field">
                <label for>Idade do amigo</label>
                <input type="text" v-model="friend.age" />
                <!-- {{ person2.friends }} -->
              </div>
              </div>
              <button type="button" @click="addFriend('person2')">adicionar amigo</button>
            </div>
            <div class="divisor">
              <h2>Jogos que já jogou</h2>
              <div class="group" v-for="game in person2.player.games">
                <div class="field">
                  <label for>Nome do jogo</label>
                  <input type="text" v-model="game.name" />
                </div>
              </div>
              <button type="button" @click="addGame('person2')">adicionar jogo já jogado</button>
            </div>
            <div class="divisor">
              <h2>Consoles bonitos</h2>
              <div class="group" v-for="cons in person2.player.consoles">
                <div class="field" >
                  <select name="" id="" v-model="cons.name">
                    <option value="">Selecione um console</option>
                    <option value="Xbox">Xbox</option>
                    <option value="Xbox 360">Xbox 360</option>
                    <option value="Xbox One">Xbox One</option>
                    <option value="Xbox One X">Xbox One X</option>
                    <option value="PS1">PS1</option>
                    <option value="PS2">PS2</option>
                    <option value="PS3">PS3</option>
                    <option value="PS4">PS4</option>
                    <option value="Nintendo Switch">Nintendo Switch</option>
                    <option value="Nintendo 64">Nintendo 64</option>
                  </select>
                </div>
              </div>
              <button type="button" @click="addConsole('person2')">adicionar console</button>
            </div>
          </form>
        </div>
        <div style="width: 50%; padding: 16px; background-color: rgba(0,255,0,0.12)">
          <code>
            <pre>
  {{ person2 }}
            </pre>
          </code>
        </div>
      </div>

      <div v-if="diffType === 'deep-diff'" style="width: 35%; padding: 16px; background-color: rgba(0,0,0,0.05)">
        <code>
          <pre>
{{ deepDiff() }}
          </pre>
        </code>
      </div>

      <div v-if="diffType ===  'deep-object-diff'" style="width: 35%; padding: 16px; background-color: rgba(0,0,0,0.05)">
        <code style="margin-bottom: 16px">
          <h3>diff</h3>
          <pre>
{{ diff() }}
          </pre>
        </code>
        <code style="margin-bottom: 16px">
          <h3>addedDiff</h3>
          <pre>
{{ addedDiff() }}
          </pre>
        </code>
        <code style="margin-bottom: 16px">
          <h3>deletedDiff</h3>
          <pre>
{{ deletedDiff() }}
          </pre>
        </code>
        <code style="margin-bottom: 16px">
          <h3>updatedDiff</h3>
          <pre>
{{ updatedDiff() }}
          </pre>
        </code>
        <code style="margin-bottom: 16px">
          <h3>detailedDiff</h3>
          <pre>
{{ detailedDiff() }}
          </pre>
        </code>
      </div>

    </div> 

  </div>
</template>

<script>
import { diff, addedDiff, deletedDiff, updatedDiff, detailedDiff } from 'deep-object-diff';
import { diff as deepDiff} from 'deep-diff';
import { def } from './def';

export default {
  name: 'home',
  data: () => ({
    birth: '1989-06-03',
    diffType: 'deep-object-diff',
    person1: {
      name: '',
      number: 0,
      birthdate: new Date(),
      friends: [],
      player: {
        games: [],
        consoles: [],
      },
    },
    person2: {
      name: '',
      number: 0,
      birthdate: new Date(),
      friends: [],
      player: {
        games: [],
        consoles: [],
      },
    },
    default: {},
  }),
  created() {
    this.setBirthdate('person1');
    this.setBirthdate('person2');
    this.default = {...this.person1};
  },
  methods: {
    setPerson1Data() {
      this.person1 = JSON.parse(JSON.stringify(def));
    },
    setPerson2Data() {
      this.person2 = JSON.parse(JSON.stringify(def));
    },
    setData() {
      this.person1 = JSON.parse(JSON.stringify(def));
      this.person2 = JSON.parse(JSON.stringify(def));
    },
    clearPerson1Data() {
      this.person1 = JSON.parse(JSON.stringify(this.default));
    },
    clearPerson2Data() {
      this.person2 = JSON.parse(JSON.stringify(this.default));
    },
    clearData() {
      this.person1 = JSON.parse(JSON.stringify(this.default));
      this.person2 = JSON.parse(JSON.stringify(this.default));
    },
    deepDiff() {
      return deepDiff(this.person1, this.person2);
    },
    diff() {
      return diff(this.person1, this.person2);
    },
    addedDiff() {
      return addedDiff(this.person1, this.person2);
    },
    deletedDiff() {
      return deletedDiff(this.person1, this.person2);
    },
    updatedDiff() {
      return updatedDiff(this.person1, this.person2);
    },
    detailedDiff() {
      return detailedDiff(this.person1, this.person2);
    },
    setBirthdate(person) {
      this[person].birthdate = new Date(this.birth);
    },
    addFriend(person) {
      this[person].friends.push(
        {
          name: '',
          age: 18,
        },
      );
    },
    addGame(person) {
      this[person].player.games.push(
        {
          name: '',
        },
      );
    },
    addConsole(person) {
      this[person].player.consoles.push(
        {
          name: '',
        },
      );
    },
  },
};
</script>

<style lang="scss">
  body {
    padding: 0;
    margin: 0;
  }

  * {
    box-sizing: border-box;
  }

  .group {
    border: 1px solid rgba(0,0,0,0.1);
    padding: 16px;
    margin-bottom: 8px;
  }

  .divisor {
    margin-bottom: 64px;
  }

  pre {
    text-align: left;
  }

  .flex {
    display: flex;
  }

  .w33p {
    width: 33%;
  }

  .field {
    width: 100%;
    margin-bottom: 32px;
    display: inline-block;
    text-align: left;

    label {
      font-size: 1.1em;
      margin-bottom: 8px;
      font-weight: 600;
      display: inline-block;
      color: rgba(0,0,0,0.54)
    }

    input, select {
      width: 100%;
      padding: 12px 16px;
      border-radius: 4px;
      border-color: rgba(0,0,0,0.1);
      outline: 0 none;
      display: inline-block;
      bor

      &:focus {
        border-color: rgb(56, 0, 102);
      }
    }
  }
</style>
