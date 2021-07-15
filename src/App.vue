<template>
  <div id="app">
    
    <div class="jumbotron jumbotron-fluid">
      <div class="container">
        <h1 class="display-4">Formulários no Vue</h1>
        <p class="lead">Treinando a manipulação de formulários</p>
      </div>
    </div>

    <div class="container">

      <div class="row">

        <!-- formulario -->
        <div class="col-sm-6">

          <h3>Dados paciente</h3>

          <form>

            <div class="form-group">
              <label>Nome:</label>
              <input type="text" 
                    class="form-control" 
                    placeholder="Seu nome"
                    v-model.lazy.trim="usuario.nome"
                    >
            </div>

            <div class="form-group">
              <label>Endereço de email:</label>
              <input type="email" 
                    class="form-control" 
                    placeholder="Seu email"
                    v-model.lazy="usuario.email">
            </div>

            <div class="form-group">
              <label>Idade:</label>
              <input type="number" 
                    class="form-control" 
                    placeholder="Sua idade"
                    v-model.number="usuario.idade">
            </div>

            <div class="form-group">

              <p>Gênero:</p>

              <div class="form-check form-check-inline">
                <input type="radio" 
                      class="form-check-input" 
                      value="Masculino"
                      v-model="usuario.genero">
                <label class="form-check-label">Masculino</label>
              </div>

              <div class="form-check form-check-inline">
                <input type="radio"
                      class="form-check-input" 
                      value="Feminino"
                      v-model="usuario.genero">
                <label class="form-check-label">Feminino</label>
              </div>

            </div>

            <div class="form-group">
              <label>Ocupação:</label>
              <select class="form-control" placeholder="Seu email">
                <option>Selecione uma opção...</option>
              </select>
            </div>  

            <div class="form-group">

              <p>Comorbidades:</p>

              <div class="form-check form-check-inline">
                <input type="checkbox" 
                      class="form-check-input" 
                      value="Asma"
                      v-model="usuario.comorbidades">
                <label class="form-check-label">Asma</label>
              </div>

              <div class="form-check form-check-inline" >
                <input type="checkbox" 
                      class="form-check-input"
                      value="Bronquite"
                      v-model="usuario.comorbidades">
                <label class="form-check-label">Bronquite</label>
              </div>

              <div class="form-check form-check-inline">
                <input type="checkbox" 
                      class="form-check-input" 
                      value="Obesidade"
                      v-model="usuario.comorbidades">
                <label class="form-check-label">Obesidade</label>
              </div>

              <div class="form-check form-check-inline">
                <input type="checkbox" 
                      class="form-check-input" 
                      value="Hipertensão"
                      v-model="usuario.comorbidades">
                <label class="form-check-label">Hipertensão</label>
              </div>

            </div>      

            <div class="form-group">
              <label>Resumo dos sintomas:</label>
              <textarea class="form-control" 
                        placeholder="Descreva seus sintomas."
                        v-model="usuario.biografia"></textarea>
            </div>

            <div class="form-group">

              <div class="form-check form-check-inline">
                <input type="checkbox" 
                      class="form-check-input"
                      true-value="Sim"
                      false-value="Não"
                      v-model="usuario.notificacoes">
                <label class="form-check-label">Receber notificações por email</label>
              </div>

            </div>

            <button class="btn btn-secondary">Resetar</button>
            <button class="btn btn-success">Enviar</button>

          </form>

        </div>

        <!-- saida -->
        <div class="col-sm-6">

          <h3>Saída</h3>

          <div class="card">

            <div class="card-header">Dados</div>

            <ul class="list-group list-group-flush">
              <li class="list-group-item"><strong>Nome:</strong>{{usuario.nome}}</li>
              <li class="list-group-item"><strong>Email:</strong> {{usuario.email}}</li>
              <li class="list-group-item"><strong>Idade:</strong> {{usuario.idade}}</li>
              <li class="list-group-item"><strong>Gênero:</strong> {{usuario.genero}}</li>
              <li class="list-group-item"><strong>Ocupação:</strong> </li>
              <li class="list-group-item">
                <strong>Comorbidades:</strong>
                  <ul>
                      <li
                        v-for="(comorbidade, i) in usuario.comorbidades"
                        :key="i">{{ comorbidade }}</li>                    
                  </ul>
                </li>
              <li class="list-group-item">
                <strong>Biografia:</strong> 
                <pre>{{usuario.biografia}}</pre></li>
              <li class="list-group-item"><strong>Receber notificações?</strong>
                {{usuario.notificacoes}}
                </li>
            </ul>

            <div class="card-header">Model</div>

            <div class="card-body">
              <pre><code>{{ usuario  }}</code></pre>
            </div>

          </div>

        </div>

      </div>

    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      usuario: {
        nome:"",
        email:"",
        idade: 35,
        biografia: "",
        genero:"",
        comorbidades:[],
        notificacoes: "Não",
      }
    }
  }
}
</script>


<style scoped>
  .btn {
    margin-right: 5px;
  }
</style>