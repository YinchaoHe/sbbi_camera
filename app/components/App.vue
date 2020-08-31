<template>
  <Page>
    <CameraPlus
      top="0"
      left="0"
      ref="CameraPlus"
      height="600"
      id="camPlus"
      saveToGallery="true"
      showCaptureIcon="true"
      showGalleryIcon="true"
      showToggleIcon="true"
      showFlashIcon="true"
      debug="true"
      enableVideo="false"
      confirmVideo="false"
      defaultCamera="front"
      @loaded="onCameraLoaded"
      @photoCapturedEvent="photoCaptured($event)"
      @errorEvent="onCameraError"
    >

	<GridLayout rows="*, auto, *" columns="*, auto, *">
		<GridLayout colSpan="3" class="bg-overlay"></GridLayout>
		<GridLayout row="1" class="bg-overlay"></GridLayout>
		<GridLayout row="1" col="2" class="bg-overlay"></GridLayout>
		<GridLayout row="2" colSpan="3" class="bg-overlay"></GridLayout>
		<Label row="1" col="1" class="overlay-label" text="📷➕"></Label>
	</GridLayout>
    </CameraPlus>
  </Page>
</template>

<script>
export default {
  methods: {
    onCameraLoaded(result) {
      this.cam = result.object;
      console.log("Camera loaded...");
    },

    onButtonCapture() {
      console.log("Take Picture");
      this.image = this.cam.takePicture({ saveToGallery: true });
    },

    photoCaptured(args) {
      console.log("ARGS - ", args);
    },
    onCameraError(err) {
      console.log(err);
    }
  }
};
</script>
