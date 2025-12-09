<script>
        import * as THREE from 'three'; 
        import * as SC from 'svelte-cubed';
    import { scale } from 'svelte/transition';

        let width = 1;
        let height = 1;
        let depth = 1;

        let spin = 0;

        SC.onFrame(() => {
            spin += 0.05;
        //    width += 0.001;
        });
</script>

<div class="controls">
    <label
    >Width:
        <input type="range" min="0.1" max="3" step="0.1" bind:value={width} />
    </label>
     <label
    >Height:
        <input type="range" min="0.1" max="3" step="0.1" bind:value={height} />
    </label>
     <label
    >Depth:
        <input type="range" min="0.1" max="3" step="0.1" bind:value={depth} />
    </label>
</div>
<SC.Canvas antialias background={new THREE.Color('grey')}>
    <SC.Mesh 
    rotation={[spin, spin, spin]}
    scale={[width, height, depth]}
       material={new THREE.MeshStandardMaterial({color:'purple'})} 
        geometry={new THREE.BoxGeometry()} 
        />
    <SC.PerspectiveCamera position={[2, 2, 2]}/>
    <SC.OrbitControls />
   <SC.AmbientLight intensity={.2} />
   <SC.DirectionalLight intensity={1.5} position={[5, 10, 7]}/>
</SC.Canvas>

<style>
    .controls {
        position: absolute;
        top: 10px;
        left: 10px;
        z-index: 10;
        background: rgba(255, 255, 255, 0.8);
        padding: 10px;
        border-radius: 5px;
    }
    label {
        display: block;
        margin-bottom: 5px;
    }
</style>