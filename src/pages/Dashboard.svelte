<script>
  import { onMount } from 'svelte';
  import {useNavigate} from 'svelte-navigator';
  import VideoPlayer from "svelte-video-player";
  //
  import store from '../store';    
  import VideosED from '../utils/videos_list';
  //const source = 'https://www.dropbox.com/s/63wi7r82mwm8gxj/5_soft_skills.mp4?raw=1';
  //const poster = 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/images/BigBuckBunny.jpg';
  const color =   'rgb(0, 255, 157)';
  const timeDisplay = true;
  const controlsOnPause = true;
  const bufferedColor = 'purple';

  let navigate = useNavigate();   

  onMount(()=>{
       if($store){
          navigate('/loginit');
       }
   });

</script>


<div class="text-center about">
  <div class="container">
    <div class="section-title center">
      <h2>Listados de las Clases</h2>
      <hr>
    </div>
    
    {#each VideosED.resources as Videos}
    <section class="row" style="padding:50px">
      <div class="col-md-6 col-sm-6 skill">
        <span>
          <VideoPlayer source={Videos.source} {color} {timeDisplay} {controlsOnPause}/>
        </span>
     </div>
     <div class="col-md-6 col-sm-6 skill">
        <span>
            <h4 style='text-transform: capitalize;'>{Videos.name}</h4>
            <p style='text-align: left; line-height: 1.5;'>{Videos.details}</p>
        </span>
     </div>
    </section>
    <hr>
    {/each}
  </div>
</div>
