<template>  
<section class="hero">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">
        Guards of Atlantis II
      </h1>
      <h2 class="subtitle">
        Hero Browser
      </h2>
    </div>
  </div>
</section>
<section>
    <div class="container">
        <nav v-for="(hero, index) in heroes.heroes" :key="index" class="panel">
            <div class="panel-heading">
                {{hero.name}}
            </div>
            <div class="panel-block">       
                <p class="character-overview">{{hero.description}}</p>
            </div>
            <div class="panel-block attribute-overview">
                <div class="columns">
                    <div class="column is-one-quarter">
                        <nav class="level">
                            <div class="level-item has-text-centered">
                                <div>
                            <p class="heading">Initiative</p>
                            <p class="title">{{hero.initiative}}</p>
                                </div>
                            </div>
                        </nav>
                    </div>
                    <div class="column  is-one-quarter">
                        <nav class="level">
                            <div class="level-item has-text-centered">
                                <div>
                            <p class="heading">Movement</p>
                            <p class="title">{{hero.movement}}</p>
                                </div>
                            </div>
                        </nav>
                    </div>
                    <div class="column is-one-quarter">
                        <nav class="level">
                            <div class="level-item has-text-centered">
                                <div>
                            <p class="heading">Attack</p>
                            <p class="title">{{hero.attack}}</p>
                                </div>
                            </div>
                        </nav>
                    </div>
                    <div class="column is-one-quarter">
                        <nav class="level">
                            <div class="level-item has-text-centered">
                                <div>
                            <p class="heading">Defense</p>
                            <p class="title">{{hero.defense}}</p>
                                </div>
                            </div>
                        </nav>
                    </div>
                </div>
            </div>

            <div class="show-cards">
                <a herf="#" v-on:click="hero.showCards = !hero.showCards">{{hero.showCards == false ? 'view cards' : 'hide cards' }}</a>
            </div>
            <div v-show="hero.showCards">
                <div class="panel-block">
                    <div class="columns">  
                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-gold">
                                    {{ goldCard(index).name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ goldCard(index).initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in goldCard(index).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">

                                <div class="panel-heading panel-heading-silver">
                                    {{ silverCard(index).name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ silverCard(index).initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in silverCard(index).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-purple">
                                    {{ purpleCard(index).name }}
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in purpleCard(index).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Start Red Cards -->
                <div class="panel-block">
                    <div class="columns is-multiline">
                        
                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-red">
                                    {{ redCards(index).find(c => c.level === 1).name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ redCards(index).find(c => c.level === 1).initiative}}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in redCards(index).find(c => c.level === 1).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-red">
                                    {{ redCards(index).find(c => c.level === 2 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ redCards(index).find(c => c.level === 2 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in redCards(index).find(c => c.level === 2 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-red">
                                    {{ redCards(index).find(c => c.level === 3 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ redCards(index).find(c => c.level === 3 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in redCards(index).find(c => c.level === 3 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-red">
                                    {{ redCards(index).find(c => c.level === 2 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ redCards(index).find(c => c.level === 2 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in redCards(index).find(c => c.level === 2 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-red">
                                    {{ redCards(index).find(c => c.level === 3 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ redCards(index).find(c => c.level === 3 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in redCards(index).find(c => c.level === 3 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
                <!-- end red cards -->

                <!-- Start blue Cards -->
                <div class="panel-block">
                    <div class="columns is-multiline">
                        
                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-blue">
                                    {{ blueCards(index).find(c => c.level === 1).name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ blueCards(index).find(c => c.level === 1).initiative}}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in blueCards(index).find(c => c.level === 1).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-blue">
                                    {{ blueCards(index).find(c => c.level === 2 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ blueCards(index).find(c => c.level === 2 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in blueCards(index).find(c => c.level === 2 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-blue">
                                    {{ blueCards(index).find(c => c.level === 3 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ blueCards(index).find(c => c.level === 3 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in blueCards(index).find(c => c.level === 3 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-blue">
                                    {{ blueCards(index).find(c => c.level === 2 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ blueCards(index).find(c => c.level === 2 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in blueCards(index).find(c => c.level === 2 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-blue">
                                    {{ blueCards(index).find(c => c.level === 3 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ blueCards(index).find(c => c.level === 3 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in blueCards(index).find(c => c.level === 3 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
                <!-- end blue cards -->

                <!-- Start green Cards -->
                <div class="panel-block">
                    <div class="columns is-multiline">
                        
                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-green">
                                    {{ greenCards(index).find(c => c.level === 1).name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ greenCards(index).find(c => c.level === 1).initiative}}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in greenCards(index).find(c => c.level === 1).skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-green">
                                    {{ greenCards(index).find(c => c.level === 2 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ greenCards(index).find(c => c.level === 2 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in greenCards(index).find(c => c.level === 2 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-green">
                                    {{ greenCards(index).find(c => c.level === 3 && c.path === 'primary').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ greenCards(index).find(c => c.level === 3 && c.path === 'primary').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in greenCards(index).find(c => c.level === 3 && c.path === 'primary').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                            </div> 
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-green">
                                    {{ greenCards(index).find(c => c.level === 2 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ greenCards(index).find(c => c.level === 2 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in greenCards(index).find(c => c.level === 2 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                        <div class="column is-one-third">
                            <div class="panel">
                                <div class="panel-heading panel-heading-green">
                                    {{ greenCards(index).find(c => c.level === 3 && c.path === 'alternate').name }}
                                </div>
                                <div class="panel-block panel-block-skills">       
                                    <p><label>Initiative:</label> {{ greenCards(index).find(c => c.level === 3 && c.path === 'alternate').initiative }}</p>
                                </div>
                                <div class="panel-block panel-block-skills" v-for="(skill, index) in greenCards(index).find(c => c.level === 3 && c.path === 'alternate').skills" :key=index>
                                    <div><label>Rank: </label>{{ skill.rank }}</div>
                                    <div v-if="skill.skillType"><label>Skill Type: </label>{{ skill.skillType }} </div>
                                    <div v-if="skill.area"><label>Area: </label><span v-html="skill.area"></span></div>
                                    <div v-if="skill.range"><label>Range: </label><span v-html="skill.range"></span></div>
                                    <div v-if="skill.value"><label>Value: </label>{{ skill.value }}</div>
                                    <div v-if="skill.text"><label>Text: </label><span v-html="skill.text"></span></div>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
                <!-- end green cards -->
            </div>
        </nav>
    </div>
</section>
</template>

<script>

import heroes from '../data/heroes'

export default {
  name: 'Home',
  props: {
    msg: String
  },
  data() {
      return {
        heroes
      }
  },
  methods: {
        goldCard(index) {
        return this.heroes.heroes[index].cards.find(c => c.cardType==='gold') 
        },
        silverCard(index) {
            return this.heroes.heroes[index].cards.find(c => c.cardType==='silver')
        },
        purpleCard(index) {
            return this.heroes.heroes[index].cards.find(c => c.cardType==='purple')
        },
        redCards(index) {
            return this.heroes.heroes[index].cards.filter(c => c.cardType==='red')
        },
        blueCards(index) {
            return this.heroes.heroes[index].cards.filter(c => c.cardType==='blue')
        },
        greenCards(index) {
            return this.heroes.heroes[index].cards.filter(c => c.cardType==='green')
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .columns {
        width: 100%;
    }

    p.title {
        font-size: 20px;
    }

    .panel-heading-gold {
        background-color: gold;
    }

    .panel-heading-silver {
        background-color: silver;
    }

    .panel-heading-purple {
        background-color: purple;
        color:#eee;
    }

    .panel-heading-red {
        background-color: darkred;
        color:#eee;
    }

    .panel-heading-blue {
        background-color: darkblue;
        color:#eee;
    }

    .panel-heading-green {
        background-color: darkgreen;
        color:#eee;
    }

    .panel-block-skills {
        display: block;
    }

    .panel-block-skills label {
        font-weight: bold;
    }

    .attribute-overview {
        padding-bottom: 25px;
        padding-top: 20px;
        margin-bottom: 20px;
    }

    .character-overview {
        padding-left: 10px;
        font-size: 18px;
        margin-bottom: 10px;
        margin-top: 10px;
    }

    .card-block {
        display: none;
    }

    .show-cards {
        text-align: center;
        font-size: 18px;
        padding-bottom: 20px;
    }

    .blue-dot {  
        height: 10px;
        width: 10px;
        background-color: blue;
        color: blue;
        border-radius: 50%;
        display: inline-block;
    }

    .red-dot {  
        height: 10px;
        width: 10px;
        background-color: red;
        color: red;
        border-radius: 50%;
        display: inline-block;
    }

</style>
