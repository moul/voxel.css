#voxel.css

[![GuardRails badge](https://badges.production.guardrails.io/moul/voxel.css.svg)](https://www.guardrails.io)

#### JavaScript 3D library ####

The goal of this project is to provide a lightweight 3D CSS library with very simple implementation.

[Demo](http://voxelcss.com/demo) — [Documentation](./docs)


### Usage ###

Download the [minified library](./dist/voxelcss.js) and [css file](./dist/voxel.css) and include both in your html.

```html
<script src="js/voxelcss.js"></script>
<link rel='stylesheet' href="css/voxel.css"></link>
```

This code creates a scene, a savable world, and an editor that allow you to immediately begin building worlds with voxel.css and see how little code is required to make complex 3D voxel games. If you've built anything in the past it auto-loads your previous build instead of creating a new one.

```html
<script>

	var scene, world, editor;

	init();

	function init() {
	scene = new voxelcss.Scene();
	scene.rotate(-Math.PI / 8, Math.PI / 4, 0);
	scene.attach(document.body);

	var lightSource = new voxelcss.LightSource(300, 300, 300, 750, 0.3, 1);
	scene.addLightSource(lightSource);

	world = new voxelcss.World(scene);
	editor = new voxelcss.Editor(world);
	editor.enableAutoSave();

	editor.load();
	if(world.getVoxels().length === 0)
	  editor.add(new voxelcss.Voxel(0, 0, 0, 100, {
		mesh: voxelcss.Meshes.grass
	  }));
	}

</script>
```
If everything went well you should see [this](http://jsfiddle.net/hjlarco/rrvsL9h6/).


### Core Concepts ###

There are 4 important classes. Scene, World, Editor and of course Voxel. The destinctions between a Scene, World, and Editor are important to know if you are to leverage them well. A Scene is simply a camera. It can rotate, pan, zoom, and contain voxels. Meanwhile a World can save the state of any voxels added to it. This is important as voxels that are in a scene but not in a world are not savable. Lastly the Editor creates all the mouse events necessary to add the user to add and remove blocks from a World with the added option to autosave all changes.


### Properties and Classes ###

[Core Classes](./docs/Core) — [Interfaces](./docs/Interfaces)


### Change log ###

[releases](https://github.com/HunterLarco/voxel.css/releases)

