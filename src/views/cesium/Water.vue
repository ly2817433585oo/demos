<template>
  <div class="map-container"></div>
</template>

<script>
import * as Cesium from "cesium/Cesium";
import "cesium/Widgets/widgets.css";
import subMerge from "./JS/subMerge.js";


export default {
  name: "Cesium-Demo1",
  data() {
    return {
      token:
        "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI2YTA2NDczYy0yZDI5LTRlZDQtYjc2MS04ODFlNjVhM2MzNmEiLCJpZCI6MzI5MTUsInNjb3BlcyI6WyJhc3IiLCJnYyJdLCJpYXQiOjE1OTc3MzQ0Njh9.6zIb_oq2-csQajtsY7YD1DzrKicgslmWNu2B3WEwa08",
      viewerOption: {
        geocoder: false, //地理位置查询定位控件
        homeButton: true, //默认相机位置控件
        timeline: true, //时间滚动条控件
        navigationHelpButton: false, //默认的相机控制提示控件
        fullscreenButton: false, //全屏控件
        scene3DOnly: true, //每个几何实例仅以3D渲染以节省GPU内存
        baseLayerPicker: true, //底图切换控件
        animation: false, //控制场景动画的播放速度控件
        shouldAnimate: true,
      },
      viewer: null,
      url: "http://10.35.11.170/cesium/",
      viewModel: {
        show: true,
        intensity: 2.0,
        distortion: 10.0,
        dispersion: 0.4,
        haloWidth: 0.4,
        dirtAmount: 0.4,
      },
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      var mapboxtoken =
        "pk.eyJ1IjoibG9ja2luOTgiLCJhIjoiY2tkemVxOGt3M2x0bzJ5bWhmZW9zdHMzciJ9.ezS0gefnTxsnv7D1ojZM7w";
      Cesium.Ion.defaultAccessToken = this.token;
      let viewer = new Cesium.Viewer(this.$el, this.viewerOption);
      viewer._cesiumWidget._creditContainer.style.display = "none"; //隐藏版权
      // this.viewer = viewer;
      viewer.camera.flyHome(0);

      var scene = viewer.scene;
      scene.globe.depathTestAgainstTerrain = true;
      scene.camera.setView({
        destination: Cesium.Cartesian3.fromDegrees(
          107.33031,
          30.068813,
          1500.0
        ),
        orientation: {
          heading: Cesium.Math.toRadians(0.0),
          pitch: Cesium.Math.toRadians(-20),
          roll: Cesium.Math.toRadians(0),
        },
      });

      viewer.scene.globe.depthTestAgainstTerrain = false;
      var polygonWithHole = new Cesium.PolygonGeometry({
        polygonHierarchy: new Cesium.PolygonHierarchy(
          // Cesium.Cartesian3.fromDegreesArray([106, 32, 107, 32, 107, 33, 106, 32])//,
          Cesium.Cartesian3.fromDegreesArray([
            100,
            20,
            133,
            20,
            133,
            35,
            100,
            35,
          ]),
          [
            new Cesium.PolygonHierarchy(
              Cesium.Cartesian3.fromDegreesArray([
                126.5013885498,
                37.5944366455,
                126.5138931274,
                37.5972137451,
                126.5394287109,
                37.6277694702,
                126.5166549683,
                37.7584686279,
                126.5122146606,
                37.7679100037,
                126.4978942871,
                37.7781867981,
                126.4436035156,
                37.8063430786,
                126.4358062744,
                37.8162460327,
                126.4241485596,
                37.821521759,
                126.3987426758,
                37.8177757263,
                126.3673477173,
                37.7874984741,
                126.364151001,
                37.7202682495,
                126.3730316162,
                37.6231842041,
                126.3841552734,
                37.6070785522,
                126.3974914551,
                37.5988769531,
                126.41456604,
                37.5931854248,
                126.4485931396,
                37.5922164917,
                126.5013885498,
                37.5944366455,
              ])
            ),
            new Cesium.PolygonHierarchy(
              Cesium.Cartesian3.fromDegreesArray([
                121.4515151978,
                39.4446411133,
                121.4428939819,
                39.4624938965,
                121.4305419922,
                39.4708251953,
                121.4140167236,
                39.4766540527,
                121.3930511475,
                39.4791564941,
                121.3371963501,
                39.4785995483,
                121.2633285522,
                39.435962677,
                121.2558288574,
                39.4094314575,
                121.2590179443,
                39.3804092407,
                121.2824935913,
                39.3805465698,
                121.2980270386,
                39.3899917603,
                121.3819274902,
                39.3691558838,
                121.4094161987,
                39.3613815308,
                121.42137146,
                39.3655471802,
                121.4349822998,
                39.3887443542,
                121.4515151978,
                39.4446411133,
              ])
            ),
            new Cesium.PolygonHierarchy(
              Cesium.Cartesian3.fromDegreesArray([
                133,
                35.5174428508,
                132.9612121582,
                35.4941596985,
                132.9291381836,
                35.4955444336,
                132.8866577148,
                35.4966583252,
                132.8660583496,
                35.496383667,
                132.8530273438,
                35.4949951172,
                132.8296813965,
                35.4888839722,
                132.6810913086,
                35.4405441284,
                132.6336517334,
                35.4211044312,
                132.6299591064,
                35.4077682495,
                132.6416625977,
                35.3988800049,
                132.6669311523,
                35.3880462646,
                132.678314209,
                35.3816604614,
                132.6813659668,
                35.3690223694,
                132.6746826172,
                35.3463821411,
                132.6649780273,
                35.320274353,
                132.6588745117,
                35.3086013794,
                132.6519165039,
                35.2986068726,
                132.638885498,
                35.2863845825,
                132.6293945313,
                35.2799911499,
                132.61328125,
                35.2719345093,
                132.5957946777,
                35.2674942017,
                132.5794067383,
                35.2611083984,
                132.5472106934,
                35.2474899292,
                132.4147033691,
                35.172077179,
                132.4046936035,
                35.1613769531,
                132.3983154297,
                35.1505432129,
                132.3596801758,
                35.0999984741,
                132.3166503906,
                35.0516586304,
                132.299987793,
                35.0361099243,
                132.2888793945,
                35.0319366455,
                132.2477416992,
                35.0211029053,
                132.2157897949,
                35.0074996948,
                132.1307983398,
                34.9499969482,
                132.0988464355,
                34.9261016846,
                132.0769195557,
                34.9030456543,
                132.0519104004,
                34.8680496216,
                131.8453826904,
                34.7027702332,
                131.8327331543,
                34.6960983276,
                131.8163757324,
                34.6897125244,
                131.7805480957,
                34.6819381714,
                131.7444152832,
                34.6741638184,
                131.6802062988,
                34.6622085571,
                131.6230163574,
                34.6558227539,
                131.6038513184,
                34.6536026001,
                131.5910644531,
                34.6419372559,
                131.5546875,
                34.6033248901,
                131.4136047363,
                34.4516601562,
                131.4060974121,
                34.422077179,
                131.3166503906,
                34.388885498,
                131.2627563477,
                34.3769378662,
                131.2100982666,
                34.3703384399,
                131.2119140625,
                34.3983306885,
                131.1655273438,
                34.4172134399,
                130.9766235352,
                34.428604126,
                130.9649658203,
                34.4252700806,
                130.9446868896,
                34.4138793945,
                130.9363708496,
                34.4011001587,
                130.8796691895,
                34.2930526733,
                130.8840026855,
                34.2602729797,
                130.9060974121,
                34.2338790894,
                130.9122009277,
                34.2252655029,
                130.9246826172,
                34.1913757324,
                130.9277648926,
                34.1813812256,
                130.9237365723,
                34.1663818359,
                130.8949890137,
                34.133605957,
                130.886932373,
                34.1252670288,
                130.8844299316,
                33.9344329834,
                130.8933105469,
                33.921661377,
                130.9051208496,
                33.9137382507,
                130.9169158936,
                33.9166603088,
                130.980255127,
                33.9760971069,
                130.9909210205,
                33.9886016846,
                130.9977264404,
                34.007358551,
                131.0303955078,
                34.0395812988,
                131.059967041,
                34.0338821411,
                131.0921936035,
                34.0208282471,
                131.108581543,
                34.0113830566,
                131.1480407715,
                33.9802703857,
                131.1638793945,
                33.9536056519,
                131.1647033691,
                33.942489624,
                131.1726074219,
                33.9322166443,
                131.25831604,
                33.9184684753,
                131.3244018555,
                33.9466552734,
                131.3349609375,
                33.9516601563,
                131.3960876465,
                33.9763793945,
                131.604675293,
                34.0297164917,
                131.7457885742,
                34.053604126,
                131.7872009277,
                34.0433273315,
                131.8241271973,
                34.0165214539,
                131.8366394043,
                33.9974899292,
                132.0485839844,
                33.8952713013,
                132.068572998,
                33.8058242798,
                132.0377502441,
                33.7711029053,
                132.0505371094,
                33.7724914551,
                132.0607910156,
                33.7772140503,
                132.1433105469,
                33.826385498,
                132.1545562744,
                33.834854126,
                132.1537475586,
                33.8569869995,
                132.1323699951,
                33.9085006714,
                132.1295318604,
                33.9414710999,
                132.1792449951,
                33.9507446289,
                132.1970214844,
                33.9649124146,
                132.2132873535,
                33.9905471802,
                132.2396850586,
                34.1488800049,
                132.2410583496,
                34.1611022949,
                132.2374572754,
                34.1763839722,
                132.2325744629,
                34.19190979,
                132.2249450684,
                34.2363777161,
                132.322479248,
                34.3341598511,
                132.3363647461,
                34.3441543579,
                132.3539886475,
                34.3534660339,
                132.3706512451,
                34.3592987061,
                132.3985900879,
                34.364440918,
                132.4087219238,
                34.3645782471,
                132.5038757324,
                34.3224945068,
                132.5004119873,
                34.2931900024,
                132.5504608154,
                34.1919326782,
                132.570526123,
                34.1894302368,
                132.6321716309,
                34.1952667236,
                132.6542816162,
                34.1981811523,
                132.6905212402,
                34.2070770264,
                132.7649841309,
                34.2316589355,
                132.7749023438,
                34.2411727905,
                132.7685852051,
                34.2547149658,
                132.7802734375,
                34.2708282471,
                132.8096923828,
                34.3030471802,
                132.8201141357,
                34.3079071045,
                132.9019165039,
                34.3155441284,
                133,
                34.3213984677,
                133,
                35.5174428508,
              ])
            ),
          ]
        ),
      });
      var chinaocean = Cesium.PolygonGeometry.createGeometry(polygonWithHole);
      var watermaterial = new Cesium.Material({
        fabric: {
          type: "Water",
          uniforms: {
            baseWaterColor: new Cesium.Color(89 / 255, 148 / 255, 236 / 255, 1),
            blendColor: new Cesium.Color(0.5, 1.0, 0.699, 1.0),
            // normalMap: "../../assets/img/waterNormals.jpg",
            normalMap: this.url + "waterNormals.jpg",
            frequency: 2000,
            animationSpeed: 0.01,
            amplitude: 10.0,
            specularIntensity: 2,
            fadeFactor: 2.0,
          },
        },
      });
      var polygonPrimitive = new Cesium.GeometryInstance({
        geometry: polygonWithHole,
        id: "chinaocean",
        attributes: {
          color: new Cesium.ColorGeometryInstanceAttribute(0.0, 1.0, 1.0, 0.5),
        },
      });

      viewer.scene.primitives.add(
        new Cesium.Primitive({
          geometryInstances: polygonPrimitive,
          appearance: new Cesium.EllipsoidSurfaceAppearance({
            material: watermaterial,
          }),
        })
      );
    },
    drawOcean() {
     
    },
  },
};
</script>

<style>
</style>