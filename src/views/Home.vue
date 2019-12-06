<template>
  <div class="home">

    <div class="g-button" style="padding: 16px">
      <button @click="diffType = 'deep-diff'" :class="{'active' : diffType === 'deep-diff'}" >Deep diff npm package</button>
      <button @click="diffType = 'deep-object-diff'" :class="{'active' : diffType === 'deep-object-diff'}" >Deep object diff npm package</button>
      <button @click="diffType = 'return-deep-diff'" :class="{'active' : diffType === 'return-deep-diff'}" >Return deep diff npm package</button>
    </div>

    <div v-if="diffType === 'deep-diff'">
      <h1 style="margin: 0">Deep diff</h1>
      <a href="https://www.npmjs.com/package/deep-diff">npmjs.com/deep-diff</a>
    </div>

    <div v-if="diffType === 'deep-object-diff'">
      <h1 style="margin: 0">Deep object diff</h1>
      <a href="https://www.npmjs.com/package/deep-object-diff">npmjs.com/deep-object-diff</a>
    </div>

    <div v-if="diffType === 'return-deep-diff'">
      <h1 style="margin: 0">Return deep diff</h1>
      <a href="https://www.npmjs.com/package/return-deep-diff">npmjs.com/return-deep-diff</a>
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
      <div class="flex" style="flex-wrap: wrap; background-color: rgba(0,0,0,0.05)">
        <h3 style="width: 100%; flex-shrink: 0">Person 1</h3>
        <div style="width: 50%; padding: 16px;">
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
              <h3>Lista de amigos</h3>
              <div class="group" v-for="(friend, index) in person1.friends">
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
                <div style="margin-top: 48px">
                  <h3>Jogos que {{ friend.name || 'amigo' }} já jogou</h3>
                  <div class="group" v-for="game in friend.games">
                    <div class="field">
                      <label for>Nome do jogo</label>
                      <input type="text" v-model="game.name" />
                    </div>
                  </div>
                  <button type="button" @click="addFriendGame('person1', index)">adicionar jogo já jogado do amigo</button>
                </div>
              </div>
              <button type="button" @click="addFriend('person1')">adicionar amigo</button>
            </div>
            <div class="divisor">
              <h3>Jogos que {{ person1.name || 'pessoa' }} já jogou</h3>
              <div class="group" v-for="game in person1.player.games">
                <div class="field">
                  <label for>Nome do jogo</label>
                  <input type="text" v-model="game.name" />
                </div>
              </div>
              <button type="button" @click="addGame('person1')">adicionar jogo já jogado</button>
            </div>
            <div class="divisor">
              <h3>Consoles bonitos</h3>
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

      <div class="flex" style="flex-wrap: wrap; background-color: rgba(0,255,0,0.12)">
        <h3 style="width: 100%; flex-shrink: 0">Person 1</h3>
        <div style="width: 50%; padding: 16px;">
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
              <h3>Lista de amigos</h3>
              <div class="group" v-for="(friend, index) in person2.friends">
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
                <div style="margin-top: 48px">
                  <h3>Jogos que {{ friend.name || 'amigo' }} já jogou</h3>
                  <div class="group" v-for="game in friend.games">
                    <div class="field">
                      <label for>Nome do jogo</label>
                      <input type="text" v-model="game.name" />
                    </div>
                  </div>
                  <button type="button" @click="addFriendGame('person2', index)">adicionar jogo já jogado do amigo</button>
                </div>
              </div>
              <button type="button" @click="addFriend('person2')">adicionar amigo</button>
            </div>
            <div class="divisor">
              <h3>Jogos que {{ person2.name || 'pessoa' }} já jogou</h3>
              <div class="group" v-for="game in person2.player.games">
                <div class="field">
                  <label for>Nome do jogo</label>
                  <input type="text" v-model="game.name" />
                </div>
              </div>
              <button type="button" @click="addGame('person2')">adicionar jogo já jogado</button>
            </div>
            <div class="divisor">
              <h3>Consoles bonitos</h3>
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

      <div style="width: 35%; padding: 0 16px; background-color: rgba(255,0,0,0.05)">
        <h3 style="width: 100%; flex-shrink: 0">Diff (using {{ diffType }})</h3>
        <div v-if="diffType === 'deep-diff'">
          <code>
            <pre>
{{ ddeepDiff() }}
            </pre>
          </code>
        </div>

        <div v-if="diffType === 'return-deep-diff'" style="width: 35%; padding: 16px; background-color: rgba(0,0,0,0.05)">
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

  </div>
</template>

<script>
import { diff, addedDiff, deletedDiff, updatedDiff, detailedDiff } from 'deep-object-diff';
import deepDiff from 'return-deep-diff';
import { diff as ddeepDiff} from 'deep-diff';
import { def } from './def';

export default {
  name: 'home',
  data: () => ({
    birth: '1989-06-03',
    diffType: 'deep-diff',
    person1: {
      name: '',
      number: '0',
      birthdate: new Date(),
      friends: [],
      player: {
        games: [],
        consoles: [],
      },
    },
    person2: {
      name: '',
      number: '0',
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
    ddeepDiff() {
      return ddeepDiff(this.person1, this.person2);
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
          age: '18',
          games: [],
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
    addFriendGame(person, i) {
      this[person].friends[i].games.push(
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

$color: rgb(56, 0, 102);

  button {
    padding: 8px 16px;
    font-size: 13px;
    background-color: transparent;
    border-radius: 4px;
    border: 1px solid rgba($color, .1);
    text-transform: uppercase;
    font-weight: 600;
    color: $color;
    margin-left: 2px;
    margin-right: 2px;
    cursor: pointer;
    transition: all 200ms;
    outline: 0 none;

    &:hover {
      background-color: rgba($color, .05)
    }

    &.active {
      background-color: $color;
      color: #fff;
    }
  }

  .g-button {
    button {
      margin: 0 -1px 0 0;
      border-radius: 0;

      &:first-child {
        border-radius: 4px 0 0 4px;
      }
      &:last-child {
        border-radius: 0 4px 4px 0;
      }
    }
  }

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
    align-items: flex-start;
  }

  .w33p {
    width: 33%;
  }

  .field {
    width: 100%;
    margin-bottom: 32px;
    display: inline-block;
    text-align: left;

    .group > & {
      margin: 0;

      & + .field {
        margin-top: 32px
      }
    }

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
        border-color: $color;
      }
    }
  }
</style>
