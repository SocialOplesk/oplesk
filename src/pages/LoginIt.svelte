<script>
    import {Link, useNavigate} from 'svelte-navigator';
    import * as EmailValidator from 'email-validator';
    import axios from 'axios';
    //import * as jQ from 'jquery';
    //
    import {doLogin} from '../store';    
   
    let email;
    let pass;
    let errorLogin;
    let endpoint = 'https://script.google.com/macros/s/AKfycbxjbD02RhZFlNW7LNg1ivvZWZpiXOELh67jEbkOa6LkbCBRY8SW/exec';
 
    let navigate = useNavigate();   

    let login = async () =>{
      let emailIsValidate = EmailValidator.validate(email);
      let emailIsNotEmpty = (typeof email !== 'undefined')?true:false; 
      let passIsNotEmpty = (typeof pass !== 'undefined')?true:false; 
      //montilla269453
      if(
        (emailIsNotEmpty)&&
        (passIsNotEmpty)&&
        (emailIsValidate)
       ){
        try{
        let res = await axios.post(endpoint.concat('?email='+email+'&'+'pass='+pass));
        email = res.data.email;
        errorLogin = res.data.error;
        doLogin(errorLogin);
        navigate('/dashboard');  
        //console.log('form email: ',email);         
        //console.log('form error: ',errorLogin);         
     }catch(err){
         console.log(err);
     }   

       }          
    }
</script>


<div id="about">
  <div class="login_container">
    <div class="section-title text-center center"> 
        <h2>Curso de RRHH IT</h2>
        <hr>
    </div>
    <form>
      <div class="form-group">
        <label for="correo" style="font-size:15px">💌 Correo</label>
        <input bind:value={email} 
          type="email"
          class="form-control"
          placeholder="alias@ejemplo.com"
        />
      </div>
      <div class="form-group">
        <label for="clave" style="font-size:15px">🔑 Clave</label>
        <input bind:value={pass}
          type="password"
          class="form-control"
          placeholder=""
        />
      </div>
      <button on:click|preventDefault={login} class="btn btn-primary">Entrar</button>
    </form>
  </div>
</div>


<style>
 .login_container {
    padding-right: 400px;
    padding-left: 400px;
    margin-right: auto;
    margin-left: auto;
}
</style>