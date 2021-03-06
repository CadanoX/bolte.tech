<template>
  <v-container fluid grid-list-lg mt-n2 height="100%">
    <v-row justify-center align-center height="100%" pa-6 ma-0>
      <v-col v-for="pub in bibtexParsed" :key="pub.BIBTEXKEY" cols="12">
        <publication :bibtex="pub" v-bind="meta[pub.BIBTEXKEY]" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Publication from '../components/Publication.vue';

export default {
  components: { Publication },
  data() {
    return {
      meta: {
        trautner2020sunspotplots: {
          image: require('../../assets/images/sunspotGeo.png'),
          video:
            'https://vis.uib.no/wp-content/papercite-data/vids/Trautner_2020_SunspotPlots_video.mp4'
        },
        bolte2020orcha: {
          image: require('../../assets/images/orcha.jpg')
        },
        bolte2020splitstreams: {
          image: require('../../assets/images/streams.png')
        },
        bolte2020visavis: {
          image: require('../../assets/images/source.png'),
          video: 'https://youtu.be/5XO6BU4j1KQ'
        },
        bolte2020MVS: {
          image: require('../../assets/images/measures.png'),
          abstract:
            'Measurement is an integral part of modern science, providing the fundamental means for evaluation, comparison, and prediction. In the context of visualization, several different types of measures have been proposed, ranging from approaches that evaluate particular aspects of individual visualization techniques, their perceptual characteristics, and even economic factors. Furthermore, there are approaches that attempt to provide means for measuring general properties of the visualization process as a whole. Measures can be quantitative or qualitative, and one of the primary goals is to provide objective means for reasoning about visualizations and their effectiveness. As such, they play a central role in the development of scientific theories for visualization. In this chapter, we provide an overview of the current state of the art, survey and classify different types of visualization measures, characterize their strengths and drawbacks, and provide an outline of open challenges for future research.'
        },
        ivapp19: {
          image: require('../../assets/images/streamgraph.png')
        }
      },
      bibtexParsed: {},
      bibtex: `
      @article {trautner2020sunspotplots,
        journal = {Computer Graphics Forum},
        title = {{Sunspot Plots}: {M}odel-based Structure Enhancement for Dense Scatter Plots},
        author = {Trautner, Thomas and Bolte, Fabian and Stoppel, Sergej and Bruckner, Stefan},
        year = {2020},
        volume = {39},
        number = {3},
        pages = {},
        publisher = {The Eurographics Association and John Wiley & Sons Ltd.},
        keywords = {Human-centered computing, Visualization techniques, Information visualization, Empirical studies in visualization},
        ISSN = {1467-8659},
        DOI = {10.1111/cgf.14001},
        url = {https://vis.uib.no/wp-content/papercite-data/pdfs/Trautner_2020_SunspotPlots_PDF.pdf}
      },

      @inproceedings {bolte2020orcha,
        booktitle = {Eurographics 2020 - Short Papers},
        title = {{Organic Narrative Charts}},
        author = {Bolte, Fabian and Bruckner, Stefan},
        year = {2020},
        publisher = {The Eurographics Association},
        ISSN = {1017-4656},
        ISBN = {978-3-03868-101-4},
        DOI = {10.2312/egs.20201026},
        url={https://arxiv.org/pdf/2004.13896.pdf}
      },
      
      @ARTICLE{bolte2020splitstreams,
        author={Bolte, Fabian and Nourani, Mahsan and Ragan, Eric D. and Bruckner, Stefan},
        journal={IEEE Transactions on Visualization and Computer Graphics},
        title={{SplitStreams}: {A} Visual Metaphor for Evolving Hierarchies},
        year={2020},
        doi={10.1109/TVCG.2020.2973564},
        ISSN={1077-2626},
        url={https://arxiv.org/pdf/2002.03891.pdf},
        keywords={Visualization, hierarchy data, time-varying data, streamgraphs, treemaps.}
      },

      @ARTICLE{bolte2020visavis,
        author={Bolte, Fabian and Bruckner, Stefan},
        journal={IEEE Transactions on Visualization and Computer Graphics},
        title={{Vis-a-Vis}: {V}isual Exploration of Visualization Source Code Evolution},
        year={2020},
        keywords={Visualization System and Toolkit Design;User Interfaces;Integrating Spatial and Non-Spatial Data Visualization;Software Visualization},
        doi={10.1109/TVCG.2019.2963651},
        ISSN={2160-9306},
        url = {https://arxiv.org/pdf/2001.02092.pdf}
      },

      @incollection {bolte2020MVS,
        author = {Bolte, Fabian and Bruckner, Stefan},
        title = {Measures in Visualization Space},
        booktitle = {Foundations of Data Visualization},
        chapter = {3},
        publisher = {Springer},
        year = {2020},
        note = {This is a preprint of a chapter for a planned book that was initiated by participants of the Dagstuhl Seminar 18041 ("Foundations of Data Visualization") and that is expected to be published by Springer. The final book chapter will differ from this preprint.},
        isbn = {978-3-030-34444-3},
        doi = {10.1007/978-3-030-34444-3},
        url = {https://arxiv.org/pdf/1909.05295}
      }

      @inproceedings{ivapp19,
        author={Rosenthal, Paul and Müller, Nicholas H. and Bolte, Fabian},
        title={Visual Analytics of Bibliographical Data for Strategic Decision Support of University Leaders: {A} Design Study},
        booktitle={Proceedings of the 14th International Joint Conference on Computer Vision, Imaging and Computer Graphics Theory and Applications - Volume 3: IVAPP},
        year={2019},
        pages={297-305},
        publisher={SciTePress},
        organization={INSTICC},
        doi={10.5220/0007396302970305},
        isbn={978-989-758-354-4},
        url = {https://www.paul-rosenthal.de/wp-content/uploads/2019/03/rosenthal_ivapp_2019.pdf}
      }`
    };
  },
  created() {
    const b = new BibtexParser();
    b.setInput(this.bibtex);
    b.bibtex();
    this.bibtexParsed = b.getEntries();
    console.log(this.bibtexParsed);
  }
};
</script>

<style scoped>
</style>