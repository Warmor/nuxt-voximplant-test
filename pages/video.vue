<template>
  <div><h1>Видео</h1></div>
</template>

<script>
export default {
  name: "VideoChat",
  data() {
    return {
      VoxSDK: null,
      voxImplant: null
    };
  },
  methods: {
    onSDKReady() {
      console.log("SDKReady");
      this.voxImplant.connect();
    },
    onConnectionEstablished() {
      console.log("onConnectionEstablished");
    },
    onConnectionFailed() {
      console.log("onConnectionFailed");
    },
    onConnectionClosed() {
      console.log("onConnectionClosed");
    },

    async initVoxImplant() {
      if (process.browser) {
        this.VoxSDK = await import("voximplant-websdk");
        this.voxImplant = await this.VoxSDK.getInstance();
        this.voxImplant.on(this.VoxSDK.Events.SDKReady, this.onSDKReady);
        this.voxImplant.addEventListener(this.VoxSDK.Events.ConnectionEstablished,this.onConnectionEstablished);
        this.voxImplant.addEventListener(this.VoxSDK.Events.ConnectionFailed,this.onConnectionFailed);
        this.voxImplant.addEventListener(this.VoxSDK.Events.ConnectionClosed,this.onConnectionClosed);
        await this.voxImplant.init({
          micRequired: true,
          videoSupport: true
        });
      }
    },
    async destroyVoxImplant() {
      this.voxImplant.disconnect();
      this.voxImplant.off(this.VoxImplant.Events.SDKReady);
      this.voxImplant.off(this.VoxImplant.Events.ConnectionEstablished);
      this.voxImplant.off(this.VoxImplant.Events.ConnectionFailed);
      this.voxImplant.off(this.VoxImplant.Events.ConnectionClosed);
      this.VoxSDK = null;
      this.voxImplant = null;
    }
  },
  async beforeDestroy() {
    console.log("beforeDestroy");
    await this.destroyVoxImplant();
  },
  mounted() {
    console.log("mounted");
    this.initVoxImplant();
  }
};
</script>
