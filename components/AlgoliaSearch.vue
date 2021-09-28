<template>
    <ais-instant-search
        index-name="tomsky-search-test"
        :search-client="searchClient"
    >
        <!-- <div class="left-panel">
            <ais-clear-refinements />
            <h2>Brands</h2>
            <ais-refinement-list attribute="brand" searchable />
            <ais-configure :hitsPerPage="8" />
        </div> -->
        <div class="right-panel">
            <ais-search-box />
            <ais-state-results>
                <template v-slot="{ state: { query } }">
                    <ais-hits v-show="query.length > 0">   <!-- if using v-if it will show some text as DOM has no element inside ais-hits -->
                        <template v-slot:item="{ item }">
                            <img
                                :src="item.image"
                                align="left"
                                :alt="item.name"
                            />
                            <h4>{{ item.name }}</h4>
                            <div class="hit-name">
                                <ais-highlight
                                    attribute="name"
                                    :hit="item"
                                ></ais-highlight>
                            </div>
                        </template>
                    </ais-hits>
                </template>
            </ais-state-results>

            <!-- <ais-pagination /> -->
        </div>
    </ais-instant-search>
</template>

// tomsky-search-test
// Jay s App ID   ZXE5DKLRFF    - no access without SearchAPI 

<script>
import algoliasearch from "algoliasearch/lite";
import "instantsearch.css/themes/satellite-min.css";

export default {
    name: "App",
    data() {
        return {
            searchClient: algoliasearch(
                <ALGOLIA_APP_ID>,
                <ALGOLIA_SEARCH_API>
            ),
        };
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

/* .ais-StateResults {
    display:none;
} */

.ais-Hits {
    position: absolute;
    z-index: 1;
}

.ais-Hits-list {
    margin-top: 0;
    margin-bottom: 1em;
}

.ais-InstantSearch {
    display: grid;
    grid-template-columns: 1fr 4fr;
    grid-gap: 1em;
}

/* custom styling  */
/* .ais-Hits,.ais-Pagination{
    display:block;
}  */

/* .ais-Hits-item {
    padding: 0;
    padding-left: 2rem;
} */
/* --------- */
.ais-Hits-list {
    margin-top: 0;
    margin-bottom: 1em;
}

.ais-Hits-item img {
    margin-right: 1em;
    height: 80px;
}
.hit-name {
    margin-bottom: 0.5em;
}
.hit-description {
    color: #888;
    font-size: 0.8em;
    margin-bottom: 0.5em;
}
</style>
