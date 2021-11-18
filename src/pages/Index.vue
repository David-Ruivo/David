<template>
  <q-page class="container" padding>
    
  
      <q-form
      class="row q-col-gutter-md"
      ref="myForm"
      >
        <q-input
          outlined
          clearable
          clear-icon="close"
          color="deep-blue"
          v-model="form.nome"
          label="Nome"
          class="col-md-12 col-sm-12 col-xs-12"
          :rules="[
            val => val && val.length > 2 || 'Nome obrigatório *'
          ]"
          >

          <template v-slot:prepend>
            <q-icon
              name="person"
              color="black"
            />
          </template>
        </q-input>

        <q-input
          v-model.number="form.idade"
          type="number"
          outlined
          clearable
          clear-icon="close"
          color="deep-blue"
          
          label="Idade"
          class="col-md-12 col-sm-12 col-xs-12"
          :rules="[
            val => val !== null && val !== '' || 'Idade obrigatória *',
            val => val > 6 && val < 100 || 'Coloque uma idade verdadeira'
          ]"
          unmasked-value
          >

          <template v-slot:prepend>
            <q-icon
              name="today"
              color="black"
            />
          </template>
        </q-input>

        <q-input
          v-model="form.email"
          outlined
          clearable
          clear-icon="close"
          color="deep-blue"
          
          label="Email"
          class="col-md-12 col-sm-12 col-xs-12"
          :rules="[
            val => val && val.length > 1 || 'Email obrigatório *'
          ]"
          >

          <template v-slot:prepend>
            <q-icon
              style="padding-left:12px"
              name="mails"
              color="black"
            />
          </template>
        </q-input>

        <q-input
          v-model.number="form.telefone"
          outlined
          clearable
          clear-icon="close"
          color="deep-blue"

          label="Número"
          class="col-md-12 col-sm-12 col-xs-12"
          mask="+351 ### ### ###"
          unmasked-value
          style="padding-bottom:12px"
        >


          <template v-slot:prepend>
            <q-icon
              name="phone"
              color="black"
            />
          </template>
        </q-input>

        <q-select
            outlined
            v-model="form.tipoPessoa"
            :options="optionsTipoPessoa"
            label="Tipo de Pessoa"
            class="col-md-12 col-sm-12 col-xs-12"
            clearable
            clear-icon="close"
            emit-value
            map-options
            :rules="[
            val => val && val.length > 0 || 'Escolha obrigatória *'
          ]"
          />

          <span>Sexo:</span>
          <q-option-group
          style="padding-bottom: 0px margin:0 0 0 3px"
            v-model="form.sexo"
            :options="optionsSexo"
            class="col-md-12 col-sm-12 col-xs-12"
            emit-value
            map-options
          />

        
        <div class="col-12">

            <q-btn
            style="margin:0 "
              label="Registar"
              type="submit"
              color="primary"
              class="float-right"
            />
            
          </div>
      </q-form>

  </q-page>
  <p class="text-h8 float-right" style="padding-right:20px">Copyright © 2021 - David Ruivo</p>
</template>


<script>

export default {
  name: 'PageIndex',
  data(){
    
    return {
      form:{
        nome:null,
        idade:null,
        email:null,
        telefone:null,
        tipoPessoa:null,
        sexo:"n/a",

      },

      optionsTipoPessoa:[{
          label:'Particular',
          value:'p'
          },
        {
          label:'Empresarial',
          value:'e'
        }],

      optionsSexo:[{
          label:'Masculino',
          value:'m',
          color:"blue"
          },
        {
          label:'Feminino',
          value:'f',
          color:"red"
        },
        {
          label:'Outro',
          value:"n/a",
          color:"yellow"
        }
      ]}
  }
}
</script>
