<script>
    import {Router, Route} from 'svelte-navigator';
    //
    import Home from './pages/Home.svelte';
    import SocialEducation from './pages/SocialEducation.svelte';
    import LoginIt from './pages/LoginIt.svelte';
    import Dashboard from './pages/Dashboard.svelte';
</script>

<Router>
    <Route exact path='/'><Home /></Route>
    <Route path='/rrhhit'><SocialEducation /></Route>
    <Route path='/loginit'><LoginIt /></Route>
    <Route path='/dashboard'><Dashboard /></Route>
</Router>
