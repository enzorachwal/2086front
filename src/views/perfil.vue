<template>
  <div>
    <section class="section">
        <h1 class="title">Você!</h1>
    <div class="columns">
    
        <div class="column is-4">
         <b-field class="file is-primary" :class="{'has-name': !!file}">
        <b-upload v-model="file" class="file-label">
            <span class="file-cta">
                <b-icon class="file-icon" icon="upload"></b-icon>
                <span class="file-label">Click to upload</span>
            </span>
            <span class="file-name" v-if="file">
                {{ file.name }}
            </span>
        </b-upload>
    </b-field>
        </div>
        <div class="column">
 
        <form class="box">
  <div class="field">
    <label class="label">Nome Completo</label>
    <div class="control">
  
      <input class="input" v-model='paciente.nome' >
    </div>
  </div>

  <div class="field">
    <label class="label">Tipo Sanguíneo</label>
    <div class="control">
      <input class="input" placeholder=" " v-model='paciente.sangue'>
    </div>
  </div>
    <div class="field">
    <label class="label">Idade</label>
    <div class="control">
      <input class="input" placeholder=" " v-model='paciente.idade'>
    </div>
  </div>
  <div class="field">
    <label class="label">R.G.</label>
    <div class="control">
      <input class="input" placeholder="00.000.000-0" v-model='paciente.rg'>
    </div>
  </div>
  <div class="field">
    <label class="label">CPF</label>
    <div class="control">
      <input class="input" placeholder="000.000.000-00" v-model='paciente.cpf'>
    </div>
  </div>
  <div class="field">
    <label class="label">Email</label>
    <div class="control">
      <input class="input" type="email" placeholder=" alex@example.com" v-model='paciente.email'>
    </div>
  </div>


</form>
        </div>
    </div>   
    <section class="section">
      <h1 class="title has-text-primary"> Condições Médicas Relevantes </h1>   <b-field label="">
             <b-input maxlength="200" type="textarea" v-model='paciente.condicoesMedicas'></b-input>
          </b-field>
          <div class="buttons">
             <b-button type="is-primary is-light" @click='cadastrar'>Salvar</b-button>  

          </div>  
      </section>


    </section>

       
   

  </div>
</template>

<script>
export default {
    props: ['canCancel'],
    data(){
        return {
            paciente: {

            },
        
        }
    },  
    created() {
     
      //Chama a api para buscar as cidades

    },
    methods: {
      cadastrar() {
          var self = this;
          //Chama a api para criar o usuário
          this.axios.post('create-paciente/', this.paciente).then((response) => {
            console.log(response);
            //Fecha o modal
            self.$emit('close');
            //Mostra a mensagem de sucesso
            self.$buefy.dialog.alert('Cadastro realizado com sucesso!')
          })        
      }
    }  
}
</script>