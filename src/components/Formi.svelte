<script>
    import * as yup from 'yup';
    import {Form, Message, isInvalid} from 'svelte-yup';

    let Schema = yup.object().shape({
        email:yup.string().email().required('confirmar su email'),
        password: yup.string().required('confirmar su clave')
    });
     
    let fields = {email:'', name:''};
    let submitted = false; 
    let isValid;
    let values;

</script>

