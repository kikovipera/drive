<template>
  <div class="media-create-folder">
    <v-dialog v-model="this.$store.state.showCreateFolderModal" persistent width="500px" transition="fade-transition">
      <v-card>
        <v-card-title class="grey lighten-4 title">New Folder
          <v-spacer></v-spacer>
          <v-icon>folder</v-icon>
        </v-card-title>
        <v-container>
          <v-flex>
            <v-text-field
              v-model="defaultData"
              solo
              @focus="$event.target.select()"
              autofocus
              label="Folder name"
            ></v-text-field>
          </v-flex>
        </v-container>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn flat color="error" @click="hideCreateFolderModal()">Cancel</v-btn>
          <v-btn flat color="success" @click="create()">Create</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import * as types from "./../../../store/mutation-types";

export default {
  name: "media-create-folder",
  data: () => ({
    defaultData: "Untitled Folder"
  }),

  methods: {
    hideCreateFolderModal: function() {
      this.$store.commit(types.HIDE_CREATE_FOLDER_MODAL);
    },
    create: function() {
      const foldername = this.defaultData;
      this.$store.dispatch("createDirectory", { foldername });
    }
  }
};
</script>
<style>
.confirm-text {
  text-align: left;
  font-size: 20px;
}
</style>
