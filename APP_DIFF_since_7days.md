# Diff Report (APP) - Last 7 Day(s)

## src/components/EntityLevelAuditLogs.vue

- Lines added: 53

| Line | Code                                                                                                                   |
| ---- | ---------------------------------------------------------------------------------------------------------------------- |
| 506  | `        <div`                                                                                                         |
| 507  | `          v-for="(value, key) in selectedDetails"`                                                                    |
| 508  | `          :key="key"`                                                                                                 |
| 509  | `          class="detail-item"`                                                                                        |
| 510  | `        >`                                                                                                            |
| 511  | `          <p>`                                                                                                        |
| 512  | `            <strong>{{ formatKey(key) }}: </strong>`                                                                  |
| 513  | `            <span v-html="formatValue(value)"></span>`                                                                |
| 514  | `          </p>`                                                                                                       |
| 515  | `        </div>`                                                                                                       |
| 616  | `    formatKey(key) {`                                                                                                 |
| 617  | `      return key`                                                                                                     |
| 618  | `        .replace(/_/g, " ")`                                                                                          |
| 619  | `        .replace(/([a-z])([A-Z])/g, "$1 $2")`                                                                         |
| 620  | `        .replace(/\b\w/g, (c) => c.toUpperCase());`                                                                   |
| 621  | `    },`                                                                                                               |
| 622  | `    formatValue(value) {`                                                                                             |
| 623  | `      if (!value) return "";`                                                                                         |
| 624  | `      const urlRegex = /(https?:\/\/[^\s]+)/g;`                                                                       |
| 625  | `      const formatted = String(value).replace(urlRegex, (url) => {`                                                   |
| 626  | `        let displayUrl = url;`                                                                                        |
| 627  | `        if (url.length > 50) {`                                                                                       |
| 628  | `          displayUrl =`                                                                                               |
| 629  | `            url.substring(0, 30) + "..." + url.substring(url.length - 10);`                                           |
| 630  | `        }`                                                                                                            |
| 631  | `       return`<a href="${url}" target="_blank" style="color:#409EFF; text-decoration:underline;">${displayUrl}</a>`;` |
| 632  | `      });`                                                                                                            |
| 633  | `      return formatted;`                                                                                              |
| 634  | `    },`                                                                                                               |
| 645  | `        this.automationActionFilter = "";`                                                                            |
| 646  | `        this.statusFilter = "";`                                                                                      |
| 647  | `        this.dateRange = [];`                                                                                         |
| 648  | `        this.source = "";`                                                                                            |
| 651  | `        this.userFilter = "";`                                                                                        |
| 652  | `        this.actionTypeFilter = "";`                                                                                  |
| 653  | `        this.dateRange = [];`                                                                                         |
| 654  | `        this.source = "";`                                                                                            |
| 692  | `      this.selectedDetails = null;`                                                                                   |
| 1018 | `      if (this.activeTab === "auditLogs") {`                                                                          |
| 1019 | `        this.fetchGlobalLogs();`                                                                                      |
| 1020 | `      } else if (this.activeTab === "automationLogs") {`                                                              |
| 1021 | `        this.fetchAutomationLogs();`                                                                                  |
| 1022 | `      }`                                                                                                              |
| 1028 | `      if (this.activeTab === "auditLogs") {`                                                                          |
| 1029 | `        this.fetchGlobalLogs();`                                                                                      |
| 1030 | `      } else if (this.activeTab === "automationLogs") {`                                                              |
| 1031 | `        this.fetchAutomationLogs();`                                                                                  |
| 1032 | `      }`                                                                                                              |
| 1037 | `     if (this.activeTab === "auditLogs") {`                                                                           |
| 1038 | `        this.fetchGlobalLogs();`                                                                                      |
| 1039 | `      } else if (this.activeTab === "automationLogs") {`                                                              |
| 1040 | `        this.fetchAutomationLogs();`                                                                                  |
| 1041 | `      }`                                                                                                              |

## src/components/applicationUsers/applicationUsersApprovalForms.vue

- Lines added: 11

| Line | Code                                                                    |
| ---- | ----------------------------------------------------------------------- |
| 1837 | `              rowData,`                                                |
| 1838 | `              false,`                                                  |
| 1839 | `              false,`                                                  |
| 1840 | `              true`                                                    |
| 1974 | ``                                                                      |
| 2638 | `      this.closeBulkRejectDialog();`                                   |
| 2914 | `        row.formbuilders_details_id?.allow_field_level_permissions &&` |
| 3785 | `  width: 200px;`                                                       |
| 3955 | `  .actions-menu {`                                                     |
| 3956 | `    width: 150px;`                                                     |
| 3957 | `  }`                                                                   |

## src/components/applicationUsers/applicationUsersEntities.vue

- Lines added: 8

| Line | Code                                                                   |
| ---- | ---------------------------------------------------------------------- |
| 1243 | `import moment from "moment";`                                         |
| 1244 | `import { getAllFieldsArrayFromEntity } from "../../utils/formatter";` |
| 2539 | `                selectedFilter.filters &&`                            |
| 2540 | `                selectedFilter.filters.length &&`                     |
| 2541 | `                selectedFilter.filters[0].query_type`                 |
| 2542 | `              ? selectedFilter.filters[0].query_type`                 |
| 2543 | `              : "AND";`                                               |
| 3287 | `    "$route.query.key"() {`                                           |

## src/components/applicationUsers/applicationUsersTopbar.vue

- Lines added: 6

| Line | Code                                                                                   |
| ---- | -------------------------------------------------------------------------------------- |
| 122  | `                  this.getActiveContactType &&`                                       |
| 123  | `                  this.getActiveContactType.contact_type &&`                          |
| 124  | `                  this.getActiveContactType.contact_type.login_mode === 'rbac'`       |
| 269  | `                        this.getActiveContactType &&`                                 |
| 270  | `                        this.getActiveContactType.contact_type &&`                    |
| 271  | `                        this.getActiveContactType.contact_type.login_mode === 'rbac'` |

## src/components/applicationUsers/ssoAuthenticationExternal/externalSsoComponent.vue

- Lines added: 2

| Line | Code                                                                    |
| ---- | ----------------------------------------------------------------------- |
| 52   | `        let required_params = ["company_slug", "target_url", "type"];` |
| 63   | `            type: query_params["type"],`                               |

## src/components/companyDocuments/AddEditDocument.vue

- Lines added: 140

| Line | Code                                                                                   |
| ---- | -------------------------------------------------------------------------------------- |
| 14   | `            <el-select`                                                               |
| 15   | `              v-model="fieldsFormUpload.type"`                                        |
| 16   | `              placeholder="Select Type"`                                              |
| 17   | `            >`                                                                        |
| 19   | `                v-for="(type, index) of documentTypes"`                               |
| 25   | `            <p class="error" v-if="getErrors && getErrors.type">`                     |
| 26   | `              {{ this.getErrors.type }}`                                              |
| 27   | `            </p>`                                                                     |
| 32   | `        <el-col :span="8" v-if="fieldsFormUpload.type == 'CUSTOM'">`                  |
| 35   | `            <el-select`                                                               |
| 36   | `              v-model="fieldsFormUpload.configure_type"`                              |
| 37   | `              placeholder="Select Type"`                                              |
| 38   | `            >`                                                                        |
| 40   | `                v-for="(type, index) of configureTypes"`                              |
| 46   | `            <p class="error" v-if="getErrors && getErrors.configure_type">`           |
| 47   | `              {{ this.getErrors.configure_type }}`                                    |
| 48   | `            </p>`                                                                     |
| 54   | `            <el-input`                                                                |
| 55   | `              type="text"`                                                            |
| 56   | `              v-model="fieldsFormUpload.title"`                                       |
| 57   | `              placeholder="Document Name"`                                            |
| 58   | `            ></el-input>`                                                             |
| 59   | `            <p class="error" v-if="getErrors && getErrors.title">`                    |
| 60   | `              {{ this.getErrors.title }}`                                             |
| 61   | `            </p>`                                                                     |
| 73   | `            <p class="error" v-if="getErrors && getErrors.decription">`               |
| 74   | `              {{ this.getErrors.description }}`                                       |
| 75   | `            </p>`                                                                     |
| 84   | `            <el-date-picker`                                                          |
| 85   | `              v-model="fieldsFormUpload.valid_from"`                                  |
| 86   | `              placeholder="Select From date"`                                         |
| 87   | `            ></el-date-picker>`                                                       |
| 88   | `            <p class="error" v-if="getErrors && getErrors.valid_from">`               |
| 89   | `              {{ this.getErrors.valid_from }}`                                        |
| 90   | `            </p>`                                                                     |
| 101  | `            <p class="error" v-if="getErrors && getErrors.valid_to">`                 |
| 102  | `              {{ this.getErrors.valid_to }}`                                          |
| 103  | `            </p>`                                                                     |
| 114  | `            <p class="error" v-if="getErrors && getErrors.e_signature_required">`     |
| 115  | `              {{ this.getErrors.e_signature }}`                                       |
| 116  | `            </p>`                                                                     |
| 139  | `                        <img`                                                         |
| 140  | `                          src="@/assets/img/icons/add-field.svg"`                     |
| 141  | `                          alt="icon"`                                                 |
| 142  | `                          class="img-fluid"`                                          |
| 143  | `                        />`                                                           |
| 150  | `            <el-select`                                                               |
| 151  | `              v-model="fieldsFormUpload.category"`                                    |
| 152  | `              placeholder="Select Category"`                                          |
| 153  | `            >`                                                                        |
| 155  | `                v-for="(item, index) in getAllCategories"`                            |
| 161  | `            <p class="error" v-if="getErrors && getErrors.category">`                 |
| 162  | `              {{ this.getErrors.category }}`                                          |
| 163  | `            </p>`                                                                     |
| 187  | `                        <img`                                                         |
| 188  | `                          src="@/assets/img/icons/add-field.svg"`                     |
| 189  | `                          alt="icon"`                                                 |
| 190  | `                          class="img-fluid"`                                          |
| 191  | `                        />`                                                           |
| 205  | `                v-for="(item, index) in getAllGroups"`                                |
| 211  | `            <p class="error" v-if="getErrors && getErrors.groups">`                   |
| 212  | `              {{ this.getErrors.groups }}`                                            |
| 213  | `            </p>`                                                                     |
| 232  | `                  <p>`                                                                |
| 233  | `                    {{`                                                               |
| 234  | `                      isSampleDocument`                                               |
| 235  | `                        ? "Upload sample here"`                                       |
| 236  | `                        : "Upload document here"`                                     |
| 237  | `                    }}`                                                               |
| 238  | `                  </p>`                                                               |
| 245  | `                {{ this.fieldsFormUpload.selectedFileName }}`                         |
| 248  | `            <span v-if="logoError">{{ logoError }}</span>`                            |
| 257  | `                <button`                                                              |
| 258  | `                  class="btn submit-button"`                                          |
| 259  | `                  @click="onFormSubmit"`                                              |
| 260  | `                  type="button"`                                                      |
| 261  | `                >`                                                                    |
| 262  | `                  Save File`                                                          |
| 263  | `                </button>`                                                            |
| 266  | `                <button class="btn cancel-button" type="button" @click="cancel">`     |
| 267  | `                  Cancel`                                                             |
| 268  | `                </button>`                                                            |
| 276  | `</template>`                                                                          |
| 283  | `  name: "companyDocuments-Add-EditDocument",`                                         |
| 292  | `          label: "Static Document",`                                                  |
| 296  | `          label: "Custom Document",`                                                  |
| 300  | `          label: "Requested Document",`                                               |
| 301  | `        },`                                                                           |
| 306  | `          label: "Upload PDF/Image",`                                                 |
| 310  | `          label: "Copy Word Document",`                                               |
| 311  | `        },`                                                                           |
| 324  | `        e_signature: "",`                                                             |
| 327  | `        name: "",`                                                                    |
| 330  | `        name: "",`                                                                    |
| 345  | `        disabledDate: this.disabledValidTODDate,`                                     |
| 346  | `      },`                                                                             |
| 358  | `      "getCompanyDocumentUpdateStatus",`                                              |
| 365  | `        Authorization: this.getAuthenticationDetails.access_token,`                   |
| 392  | `    },`                                                                               |
| 396  | `    AddGroup,`                                                                        |
| 429  | `        e_signature_value: "",`                                                       |
| 454  | `          message: "Document updated successfully",`                                  |
| 478  | `          message: "Document added successfully",`                                    |
| 523  | `    async beforeLogoUpload() {},`                                                     |
| 534  | `        file_size_in_kb: file.raw.size / 1000,`                                       |
| 544  | `        upload_url: this.getFileUploadURL,`                                           |
| 557  | `            : this.getNewCompanyDocument._id,`                                        |
| 566  | `            console.log("fileuploaded");`                                             |
| 592  | `        e_signature: "",`                                                             |
| 615  | `        groups: this.selectedCompanyDocument.groups.map((e) => e._id),`               |
| 626  | `        valid_to: this.selectedCompanyDocument.valid_to,`                             |
| 628  | `    },`                                                                               |
| 633  | `    this.$store.commit("companyDocuments/setFileUploadURL", null, {`                  |
| 635  | `    });`                                                                              |
| 636  | `    this.$store.commit("companyDocuments/setFileUploadRefId", null, {`                |
| 637  | `      root: true,`                                                                    |
| 638  | `    });`                                                                              |
| 639  | `    this.$store.commit("companyDocuments/setDocumentUploadStatus", null, {`           |
| 640  | `      root: true,`                                                                    |
| 641  | `    });`                                                                              |
| 642  | `    this.$store.commit("companyDocuments/setCompanyDocumentAddStatus", null, {`       |
| 643  | `      root: true,`                                                                    |
| 644  | `    });`                                                                              |
| 645  | `    //this.$store.commit("companyDocuments/setNewCompanyDocument", null,{root:true})` |
| 646  | `    this.$store.commit(`                                                              |
| 647  | `      "companyDocuments/setDocumentUploadStatusUpdated",`                             |
| 648  | `      null,`                                                                          |
| 649  | `      { root: true }`                                                                 |
| 651  | `    this.$store.commit(`                                                              |
| 652  | `      "companyDocuments/setCompanyDocumentUpdateStatus",`                             |
| 653  | `      null,`                                                                          |
| 654  | `      { root: true }`                                                                 |
| 655  | `    );`                                                                               |
| 656  | `    this.$store.commit("documentCategories/setAllCategories", null, {`                |
| 657  | `      root: true,`                                                                    |
| 658  | `    });`                                                                              |
| 659  | `    this.$store.commit("documentGroups/setAllGroups", null, {`                        |
| 660  | `      root: true,`                                                                    |
| 661  | `    });`                                                                              |
| 743  | `</style>`                                                                             |

## src/components/companyDocuments/AllDocumentsList.vue

- Lines added: 26

| Line | Code                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| 168  | `<script>`                                                                         |
| 175  | `  name: "companyDocuments-AllDocumentsList",`                                     |
| 233  | `      if (data) {`                                                                |
| 234  | `        console.log(data);`                                                       |
| 236  | `          name: "employee-documents-custom-doc-type-document-draft",`             |
| 238  | `            employee_document_id: data._id,`                                      |
| 239  | `          },`                                                                     |
| 504  | `    bus.$off("document-added");`                                                  |
| 505  | `    this.$store.commit("companyDocuments/setCompanyAllDocuments", null, {`        |
| 506  | `      root: true,`                                                                |
| 507  | `    });`                                                                          |
| 508  | `    this.$store.commit("companyDocuments/setDownloadUrl", null, { root: true });` |
| 509  | `    this.$store.commit("companyDocuments/setDownloadError", null, {`              |
| 510  | `      root: true,`                                                                |
| 511  | `    });`                                                                          |
| 512  | `    this.$store.commit("companyDocuments/setDeleteDocumentError", null, {`        |
| 513  | `      root: true,`                                                                |
| 514  | `    });`                                                                          |
| 515  | `    this.$store.commit("companyDocuments/setDocumentConfigureStatus", null, {`    |
| 516  | `      root: true,`                                                                |
| 517  | `    });`                                                                          |
| 518  | `    this.$store.commit("companyDocuments/setDocumentConfigureError", null, {`     |
| 519  | `      root: true,`                                                                |
| 520  | `    });`                                                                          |
| 521  | `  },`                                                                             |
| 525  | `<style lang="scss"></style>`                                                      |

## src/components/companyDocuments/AllGroupsList.vue

- Lines added: 265

| Line | Code                                                                                          |
| ---- | --------------------------------------------------------------------------------------------- |
| 2    | `  <section class="all-documents-groups-view">`                                               |
| 3    | `    <div v-loading="loading" class="vue-data-table-default">`                                |
| 4    | `      <el-row :gutter="20">`                                                                 |
| 5    | `        <el-col :span="18">`                                                                 |
| 6    | `          <data-tables`                                                                      |
| 7    | `            v-if="getGroupAllDocuments"`                                                     |
| 8    | `            :data="getGroupAllDocuments"`                                                    |
| 9    | `            style="width: 100%"`                                                             |
| 10   | `          >`                                                                                 |
| 11   | `            <el-table-column label="Name" id="name" sortable>`                               |
| 12   | `              <template slot-scope="scope">`                                                 |
| 13   | `                <!-- <router-link :to="{ name:'company-documents/all-groups-details'}"> -->` |
| 14   | `                <div class="doc-group">`                                                     |
| 15   | `                  <span class="pr-1">`                                                       |
| 16   | `                    <img`                                                                    |
| 17   | `                      src="@/assets/img/icons/folder-line.svg"`                              |
| 18   | `                      alt="icon"`                                                            |
| 19   | `                      class="img-fluid"`                                                     |
| 20   | `                    />`                                                                      |
| 21   | `                  </span>`                                                                   |
| 22   | `                  <h3 class="collapse-title">`                                               |
| 23   | `                    <span>`                                                                  |
| 24   | `                      <router-link`                                                          |
| 25   | `                        v-if="scope.row.total_documents > 0"`                                |
| 26   | `                        :to="{`                                                              |
| 27   | `                          name: type.toLowerCase() + '-group-data',`                         |
| 28   | `                          params: { groupId: scope.row._id },`                               |
| 29   | `                          query: { groupName: scope.row.name },`                             |
| 30   | `                        }"`                                                                  |
| 31   | `                        >{{ scope.row.name }}</router-link`                                  |
| 32   | `                      >`                                                                     |
| 33   | `                      <span class="link-disabled" v-else>{{`                                 |
| 34   | `                        scope.row.name`                                                      |
| 35   | `                      }}</span>`                                                             |
| 36   | `                    </span>`                                                                 |
| 37   | `                  </h3>`                                                                     |
| 38   | `                  <p class="categories-count">`                                              |
| 39   | `                    {{ scope.row.total_documents }}`                                         |
| 40   | `                  </p>`                                                                      |
| 42   | `                  <ul class="action-buttons pl-2">`                                          |
| 43   | `                    <li>`                                                                    |
| 44   | `                      <el-button`                                                            |
| 45   | `                        @click="onEdit(scope.row)"`                                          |
| 46   | `                        title="Update group"`                                                |
| 47   | `                      >`                                                                     |
| 48   | `                        <img src="@/assets/img/icons/create.svg" alt="icon" />`              |
| 49   | `                      </el-button>`                                                          |
| 50   | `                    </li>`                                                                   |
| 51   | `                    <li>`                                                                    |
| 52   | `                      <el-button`                                                            |
| 53   | `                        @click="onDelete(scope.row)"`                                        |
| 54   | `                        :disabled="scope.row.total_documents > 0"`                           |
| 55   | `                        :title="`                                                            |
| 56   | `                          scope.row.total_documents`                                         |
| 57   | `                            ? 'Some documents under this group'`                             |
| 58   | `                            : 'Delete group'`                                                |
| 59   | `                        "`                                                                   |
| 60   | `                      >`                                                                     |
| 61   | `                        <img src="@/assets/img/icons/delete.png" alt="icon" />`              |
| 62   | `                      </el-button>`                                                          |
| 63   | `                    </li>`                                                                   |
| 64   | `                  </ul>`                                                                     |
| 65   | `                </div>`                                                                      |
| 66   | `                <!-- </router-link> -->`                                                     |
| 67   | `              </template>`                                                                   |
| 68   | `            </el-table-column>`                                                              |
| 69   | `          </data-tables>`                                                                    |
| 70   | `        </el-col>`                                                                           |
| 71   | `        <el-col :span="6">`                                                                  |
| 72   | `          <el-card shadow="never" class="group-stats">`                                      |
| 73   | `            <div class="icon-right">`                                                        |
| 74   | `              <img`                                                                          |
| 75   | `                src="@/assets/img/icons/categories-documents.svg"`                           |
| 76   | `                class="image-icon"`                                                          |
| 77   | `                width="100px"`                                                               |
| 78   | `              />`                                                                            |
| 79   | `            </div>`                                                                          |
| 80   | `            <div class="categories-count">`                                                  |
| 81   | `              <h2>13</h2>`                                                                   |
| 82   | `              <p class="name">Categories</p>`                                                |
| 83   | `            </div>`                                                                          |
| 84   | `            <div class="categories-count">`                                                  |
| 85   | `              <h2>13</h2>`                                                                   |
| 86   | `              <p class="name">Groups</p>`                                                    |
| 87   | `            </div>`                                                                          |
| 88   | `            <div class="categories-count">`                                                  |
| 89   | `              <h2>127</h2>`                                                                  |
| 90   | `              <p class="name">Documents</p>`                                                 |
| 91   | `            </div>`                                                                          |
| 92   | `          </el-card>`                                                                        |
| 93   | `        </el-col>`                                                                           |
| 94   | `      </el-row>`                                                                             |
| 95   | `    </div>`                                                                                  |
| 96   | `    <el-dialog`                                                                              |
| 97   | `      :width="'35%'"`                                                                        |
| 98   | `      :append-to-body="true"`                                                                |
| 99   | `      :visible.sync="editGroupDialogVisible"`                                                |
| 100  | `      title="Update Group"`                                                                  |
| 101  | `      :close-on-click-modal="false"`                                                         |
| 102  | `      :close-on-press-escape="false"`                                                        |
| 103  | `    >`                                                                                       |
| 104  | `      <el-form v-model="groupForm">`                                                         |
| 105  | `        <div class="form-group">`                                                            |
| 106  | `          <el-input placeholder="Name" v-model="groupForm.name"></el-input>`                 |
| 107  | `          <p class="error" v-if="errors && errors.name">{{ errors.name }}</p>`               |
| 108  | `          <p class="error" v-if="errors && errors.critical_error">`                          |
| 109  | `            {{ this.errors.critical_error }}`                                                |
| 110  | `          </p>`                                                                              |
| 111  | `        </div>`                                                                              |
| 112  | `        <div class="form-group submit-btn-group">`                                           |
| 113  | `          <button`                                                                           |
| 114  | `            type="button"`                                                                   |
| 115  | `            class="btn submit-btn"`                                                          |
| 116  | `            @click.prevent="updateGroup"`                                                    |
| 117  | `            :disabled="disableButton"`                                                       |
| 118  | `          >`                                                                                 |
| 119  | `            submit`                                                                          |
| 120  | `          </button>`                                                                         |
| 121  | `        </div>`                                                                              |
| 122  | `      </el-form>`                                                                            |
| 123  | `    </el-dialog>`                                                                            |
| 124  | `  </section>`                                                                                |
| 127  | `<script>`                                                                                    |
| 128  | `import { mapGetters } from "vuex";`                                                          |
| 129  | `import { bus } from "../../main";`                                                           |
| 131  | `export default {`                                                                            |
| 132  | `  name: "companyDocuments-AllGroupsList",`                                                   |
| 133  | `  props: ["type"],`                                                                          |
| 135  | `  data() {`                                                                                  |
| 136  | `    return {`                                                                                |
| 137  | `      loading: false,`                                                                       |
| 138  | `      editGroupDialogVisible: false,`                                                        |
| 139  | `      selectedGroup: {},`                                                                    |
| 140  | `      groupForm: {`                                                                          |
| 141  | `        name: "",`                                                                           |
| 142  | `      },`                                                                                    |
| 143  | `      disableButton: false,`                                                                 |
| 144  | `      errors: {},`                                                                           |
| 145  | `    };`                                                                                      |
| 146  | `  },`                                                                                        |
| 147  | `  computed: {`                                                                               |
| 148  | `    ...mapGetters("documentGroups", [`                                                       |
| 149  | `      "getGroupAllDocuments",`                                                               |
| 150  | `      "getGroupUpdateStatus",`                                                               |
| 151  | `      "getGroupDeleteStatus",`                                                               |
| 152  | `      "getGroupErrors",`                                                                     |
| 153  | `    ]),`                                                                                     |
| 154  | `  },`                                                                                        |
| 155  | `  async mounted() {`                                                                         |
| 156  | `    this.fetchAllGroups();`                                                                  |
| 157  | `    bus.$on("document-added", () => {`                                                       |
| 158  | `      this.fetchAllGroups();`                                                                |
| 159  | `    });`                                                                                     |
| 160  | `  },`                                                                                        |
| 162  | `  methods: {`                                                                                |
| 163  | `    async fetchAllGroups() {`                                                                |
| 164  | `      this.loading = true;`                                                                  |
| 165  | `      await this.$store.dispatch("documentGroups/fetchGroupAllDocuments", {`                 |
| 166  | `        type: this.type ? this.type.toUpperCase() : undefined,`                              |
| 167  | `      });`                                                                                   |
| 168  | `      this.loading = false;`                                                                 |
| 169  | `    },`                                                                                      |
| 170  | `    onEdit(data) {`                                                                          |
| 171  | `      this.editGroupDialogVisible = true;`                                                   |
| 172  | `      this.selectedGroup = data;`                                                            |
| 173  | `      this.groupForm.name = this.selectedGroup.name;`                                        |
| 174  | `      this.errors = {};`                                                                     |
| 175  | `    },`                                                                                      |
| 177  | `    async onDelete(group) {`                                                                 |
| 178  | `      this.$confirm("Are you sure to delete the Group?", "Warning", {`                       |
| 179  | `        confirmButtonText: "OK",`                                                            |
| 180  | `        cancelButtonText: "Cancel",`                                                         |
| 181  | `        type: "warning",`                                                                    |
| 182  | `      }).then(() => {`                                                                       |
| 183  | `        this.deleteGroup(group);`                                                            |
| 184  | `      });`                                                                                   |
| 185  | `    },`                                                                                      |
| 187  | `    async deleteGroup(group) {`                                                              |
| 188  | `      let params = {`                                                                        |
| 189  | `        id: group._id,`                                                                      |
| 190  | `      };`                                                                                    |
| 191  | `      await this.$store.dispatch("documentGroups/deleteGroup", params);`                     |
| 192  | `      if (this.getGroupDeleteStatus) {`                                                      |
| 193  | `        this.$notify.success({`                                                              |
| 194  | `          title: "Success",`                                                                 |
| 195  | `          message: "Group deleted successfully",`                                            |
| 196  | `        });`                                                                                 |
| 197  | `        this.fetchAllGroups();`                                                              |
| 198  | `      } else {`                                                                              |
| 199  | `        this.$notify.error({`                                                                |
| 200  | `          title: "Error",`                                                                   |
| 201  | `          message: this.getGroupErrors.critial_error,`                                       |
| 202  | `        });`                                                                                 |
| 203  | `      }`                                                                                     |
| 204  | `    },`                                                                                      |
| 206  | `    async updateGroup() {`                                                                   |
| 207  | `      this.disableButton = true;`                                                            |
| 208  | `      let params = {`                                                                        |
| 209  | `        name: this.groupForm.name,`                                                          |
| 210  | `        id: this.selectedGroup._id,`                                                         |
| 211  | `      };`                                                                                    |
| 212  | `      await this.$store.dispatch("documentGroups/updateGroup", params);`                     |
| 214  | `      if (this.getGroupUpdateStatus) {`                                                      |
| 215  | `        this.$notify.success({`                                                              |
| 216  | `          title: "Success",`                                                                 |
| 217  | `          message: "Group updated successfully",`                                            |
| 218  | `        });`                                                                                 |
| 219  | `        this.editGroupDialogVisible = false;`                                                |
| 220  | `        this.fetchAllGroups();`                                                              |
| 221  | `      } else {`                                                                              |
| 222  | `        this.errors = this.getGroupErrors;`                                                  |
| 223  | `      }`                                                                                     |
| 224  | `      this.disableButton = false;`                                                           |
| 225  | `    },`                                                                                      |
| 226  | `  },`                                                                                        |
| 227  | `  beforeDestroy() {`                                                                         |
| 228  | `    this.$store.commit("documentGroups/setGroupAllDocuments", null, {`                       |
| 229  | `      root: true,`                                                                           |
| 230  | `    });`                                                                                     |
| 231  | `    this.$store.commit("documentGroups/setGroupUpdateStatus", null, {`                       |
| 232  | `      root: true,`                                                                           |
| 233  | `    });`                                                                                     |
| 234  | `    this.$store.commit("documentGroups/setGroupDeleteStatus", null, {`                       |
| 235  | `      root: true,`                                                                           |
| 236  | `    });`                                                                                     |
| 237  | `    this.$store.commit("documentGroups/setGroupErrors", null, {`                             |
| 238  | `      root: true,`                                                                           |
| 239  | `    });`                                                                                     |
| 240  | `  },`                                                                                        |
| 241  | `};`                                                                                          |
| 245  | `.all-documents-groups-view {`                                                                |
| 246  | `  .add-delete-btn {`                                                                         |
| 247  | `    button {`                                                                                |
| 248  | `      border: none;`                                                                         |
| 249  | `      padding: 0;`                                                                           |
| 250  | `      img {`                                                                                 |
| 251  | `        width: 28px;`                                                                        |
| 252  | `      }`                                                                                     |
| 253  | `    }`                                                                                       |
| 254  | `  }`                                                                                         |
| 255  | `  .categories-count {`                                                                       |
| 256  | `    margin-bottom: 0;`                                                                       |
| 257  | `  }`                                                                                         |
| 258  | `  .doc-group {`                                                                              |
| 259  | `    img {`                                                                                   |
| 260  | `      width: 25px;`                                                                          |
| 261  | `    }`                                                                                       |
| 262  | `  }`                                                                                         |
| 263  | `  .edit-delete-btn {`                                                                        |
| 264  | `    margin-left: 45px;`                                                                      |
| 265  | `    button {`                                                                                |
| 266  | `      border: none;`                                                                         |
| 267  | `      color: #fff;`                                                                          |
| 268  | `      // font-size: 1em;`                                                                    |
| 269  | `      padding: 8px;`                                                                         |
| 270  | `      &:nth-child(1) {`                                                                      |
| 271  | `        background: #2f5888;`                                                                |
| 272  | `      }`                                                                                     |
| 273  | `      &:nth-child(2) {`                                                                      |
| 274  | `        background: #f754a2;`                                                                |
| 275  | `      }`                                                                                     |
| 276  | `    }`                                                                                       |
| 277  | `  }`                                                                                         |
| 278  | `}`                                                                                           |
| 279  | `</style>`                                                                                    |

## src/components/companyDocuments/sendDocumentOnMail.vue

- Lines added: 5

| Line | Code                                                              |
| ---- | ----------------------------------------------------------------- |
| 152  | `      :documentDateFields="updateDocumentDateFields"`            |
| 169  | `      updateDocumentDateFields:null,`                            |
| 257  | `        this.updateDocumentDateFields = this.elements.filter(`   |
| 258  | `        (el) => (el.type == "DATE" \|\| el.type == "DATE_TIME")` |
| 259  | `      );`                                                        |

## src/components/companyDocuments/sendTemplateOnMail.vue

- Lines added: 5

| Line | Code                                                              |
| ---- | ----------------------------------------------------------------- |
| 150  | `      :documentDateFields="updateDocumentDateFields"`            |
| 165  | `      updateDocumentDateFields:null,`                            |
| 254  | `        this.updateDocumentDateFields = this.elements.filter(`   |
| 255  | `        (el) => (el.type == "DATE" \|\| el.type == "DATE_TIME")` |
| 256  | `      );`                                                        |

## src/components/companyDocuments/uploadDocumentModal.vue

- Lines added: 54

| Line | Code                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| 11   | `        <el-col :span="12">`                                                      |
| 22   | `              <!-- .xlsx, .xls, image/*, .doc, .docx, .ppt, .pptx, .txt,  -->`    |
| 32   | `                {{ this.fieldsFormUpload.selectedFileName }}`                     |
| 35   | `            <span v-if="logoError">{{ logoError }}</span>`                        |
| 44   | `                <el-button`                                                       |
| 45   | `                  class="btn submit-button"`                                      |
| 46   | `                  :loading="disabledButton"`                                      |
| 47   | `                  @click="addCompanyDocument"`                                    |
| 48   | `                  type="primary"`                                                 |
| 49   | `                  >Save File</el-button`                                          |
| 50   | `                >`                                                                |
| 53   | `                <button class="btn cancel-button" type="button" @click="cancel">` |
| 54   | `                  Cancel`                                                         |
| 55   | `                </button>`                                                        |
| 63   | `</template>`                                                                      |
| 68   | `  name: "companyDocuments-uploadDocumentModal",`                                  |
| 86   | `    ...mapGetters("documents", [`                                                 |
| 94   | `    ...mapGetters("s3FileUpload", ["getDocumentUploadStatus"]),`                  |
| 98   | `        Authorization: this.getAuthenticationDetails.access_token,`               |
| 102  | ``                                                                                 |
| 121  | `      } catch (err) {`                                                            |
| 148  | `      if (this.getFileUploadURL) {`                                               |
| 149  | `        this.disabledButton = false;`                                             |
| 151  | `        this.logoError = "Error in uploading file. Please try again..";`          |
| 158  | `        file_size_in_kb: file.raw.size / 1000,`                                   |
| 168  | `        upload_url: this.getFileUploadURL,`                                       |
| 179  | `          company_document_id: this.getNewCompanyDocument._id,`                   |
| 187  | `          await this.$store.dispatch(`                                            |
| 188  | `            "documents/fetchConfigureDocumentIdByDocumentId",`                    |
| 189  | `            this.getNewCompanyDocument._id`                                       |
| 190  | `          );`                                                                     |
| 191  | `          if (this.getCreateConfigureDocumentData) {`                             |
| 194  | `              message: "Document added successfully",`                            |
| 200  | `                configurable_document_id:`                                        |
| 201  | `                  this.getCreateConfigureDocumentData.configurable_document._id,` |
| 203  | `              query: this.$route.query,`                                          |
| 212  | `        this.$message("Sorry ! Error while file uploading");`                     |
| 230  | `        e_signature: "",`                                                         |
| 235  | `    this.clearFormData();`                                                        |
| 236  | `    this.$store.commit("documents/setFileUploadURL", null, { root: true });`      |
| 237  | `    this.$store.commit("documents/setFileUploadRefId", null, { root: true });`    |
| 238  | `    this.$store.commit("documents/setCompanyDocumentAddStatus", null, {`          |
| 239  | `      root: true,`                                                                |
| 240  | `    });`                                                                          |
| 242  | `    this.$store.commit("documents/setCreateConfigureDocumentData", null, {`       |
| 243  | `      root: true,`                                                                |
| 244  | `    });`                                                                          |
| 245  | `    this.$store.commit("documents/setDocumentUploadStatusUpdated", null, {`       |
| 246  | `      root: true,`                                                                |
| 247  | `    });`                                                                          |
| 248  | `    this.$store.commit("s3FileUpload/setDocumentUploadStatus", null, {`           |
| 249  | `      root: true,`                                                                |
| 250  | `    });`                                                                          |
| 331  | `</style>`                                                                         |

## src/components/customDashboard/customDashboardConfig.vue

- Lines added: 53

| Line | Code                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| 2942 | `                Show legends`                                                     |
| 2943 | `              </el-checkbox>`                                                     |
| 2945 | `            <div class="mb-1 mt-1">`                                              |
| 2947 | `                Show Expand`                                                      |
| 2948 | `              </el-checkbox>`                                                     |
| 3268 | `                  <el-table-column`                                               |
| 3269 | `                    label="Customization"`                                        |
| 3270 | `                    width="120"`                                                  |
| 3271 | `                    align="center"`                                               |
| 3272 | `                  >`                                                              |
| 3273 | `                    <template slot-scope="scope">`                                |
| 3274 | `                      <el-select`                                                 |
| 3275 | `                        v-model="scope.row.customization"`                        |
| 3276 | `                        placeholder="Select Customization"`                       |
| 3277 | `                        filterable`                                               |
| 3278 | `                        clearable`                                                |
| 3279 | `                      >`                                                          |
| 3280 | `                        <el-option`                                               |
| 3281 | `                          v-for="item in customizationOptions \|\| []"`           |
| 3282 | `                          :key="item._id"`                                        |
| 3283 | `                          :label="item.label"`                                    |
| 3284 | `                          :value="item._id"`                                      |
| 3285 | `                        />`                                                       |
| 3286 | `                      </el-select>`                                               |
| 3287 | `                    </template>`                                                  |
| 3288 | `                  </el-table-column>`                                             |
| 3391 | `    EntitiesHelper,`                                                              |
| 3772 | `        showLegend: true,`                                                        |
| 3773 | `        showExpand: true,`                                                        |
| 3887 | `      console.log("this.currentEntityFields", this.currentEntityFields);`         |
| 4564 | `      this.notifications = (component.notifications \|\| []).map((n) => ({`       |
| 4566 | `        redirect: n.redirect !== undefined ? n.redirect : true,`                  |
| 4567 | `        customization: n.customization !== undefined ? n.customization : "",`     |
| 4571 | `      if (this.notifications) {`                                                  |
| 4572 | `        this.notifications.forEach((row, i) => {`                                 |
| 4573 | `          if (row.relationship_id) {`                                             |
| 4574 | `            this.loadCustomizations(row.relationship_id).then((options) => {`     |
| 4575 | `              this.$set(this.notifications[i], "customizationOptions", options);` |
| 4576 | `            });`                                                                  |
| 4577 | `          }`                                                                      |
| 4578 | `        });`                                                                      |
| 4579 | `      }`                                                                          |
| 4614 | `        redirect: true,`                                                          |
| 4615 | `        customization: "",`                                                       |
| 4672 | `          notifications: (this.notifications \|\| []).map((n) => ({`              |
| 4674 | `            redirect: n.redirect !== undefined ? n.redirect : true,`              |
| 4675 | `            customization: n.customization !== undefined ? n.customization : "",` |
| 4723 | `      if (!("showLegends" in this.gaugeChartCustomization)) {`                    |
| 4724 | `        this.$set(this.gaugeChartCustomization, "showLegends", true);`            |
| 4725 | `      }`                                                                          |
| 4726 | `      if (!("showExpand" in this.gaugeChartCustomization)) {`                     |
| 4727 | `        this.$set(this.gaugeChartCustomization, "showExpand", true);`             |
| 4728 | `      }`                                                                          |

## src/components/customDashboard/customDashboardFormbuilderDataTable.vue

- Lines added: 71

| Line | Code                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| 322  | `                  v-if="`                                                         |
| 323  | `                    scope.row.allow_rework_on_form &&`                            |
| 324  | `                    scope.row.approval_status != 'APPROVED' &&`                   |
| 325  | `                    scope.row.approval_status != 'REJECTED'`                      |
| 326  | `                  "`                                                              |
| 330  | `                  <el-dropdown-item icon="el-icon-refresh" command="rework">{{`   |
| 331  | `                    getReworkLabel(scope.row)`                                    |
| 332  | `                  }}</el-dropdown-item>`                                          |
| 395  | `                  <span`                                                          |
| 396  | `                    v-if="`                                                       |
| 397  | `                      getApprovedUser(scope.row) &&`                              |
| 398  | `                      getApprovedUser(scope.row).approved_reason`                 |
| 399  | `                    "`                                                            |
| 400  | `                  >`                                                              |
| 401  | `                    Approved Reason:`                                             |
| 402  | `                    {{ getApprovedUser(scope.row).approved_reason }}`             |
| 403  | `                  </span>`                                                        |
| 429  | `                        <span v-if="approver.approved_reason">`                   |
| 430  | `                          <i class="el-icon-edit-outline icon-style"></i>`        |
| 431  | `                          Approved reason:`                                       |
| 432  | `                          <span class="approver-text">`                           |
| 433  | `                            {{ " " + approver.approved_reason }}`                 |
| 435  | `                        </span>`                                                  |
| 876  | `      getCompanyUsers: [],`                                                       |
| 877  | `      getAllContacts: [],`                                                        |
| 1018 | `        if (status == "approved") {`                                              |
| 1019 | `          isAllowed =`                                                            |
| 1020 | `            data.allow_revoke_for_approved \|\| data.allow_revoke_for_both;`      |
| 1021 | `        } else if (status == "rejected") {`                                       |
| 1022 | `          isAllowed =`                                                            |
| 1023 | `            data.allow_revoke_for_rejected \|\| data.allow_revoke_for_both;`      |
| 1027 | `        if (status == "approved") {`                                              |
| 1028 | `          isAllowed =`                                                            |
| 1029 | `            data.allow_revoke_for_approved_for_filler \|\|`                       |
| 1030 | `            data.allow_revoke_for_both_for_filler;`                               |
| 1031 | `        } else if (status == "rejected") {`                                       |
| 1032 | `          isAllowed =`                                                            |
| 1033 | `            data.allow_revoke_for_rejected_for_filler \|\|`                       |
| 1034 | `            data.allow_revoke_for_both_for_filler;`                               |
| 1043 | `      return row?.customization?.rework_button_name`                              |
| 1044 | `        ? row.customization.rework_button_name`                                   |
| 1045 | `        : "Rework";`                                                              |
| 1198 | `      this.closeBulkRejectDialog();`                                              |
| 1423 | `      params["is_filled_by_login_user"] =`                                        |
| 1424 | `        this.componentData?.formbuilder_user_filter == "FILLED_BY_ME"`            |
| 1425 | `          ? true`                                                                 |
| 1426 | `          : false;`                                                               |
| 1428 | `        this.componentData?.formbuilder_user_filter ==`                           |
| 1429 | `        "FILLED_BY_BUSINESS_CONTACTS"`                                            |
| 1432 | `        params["account_data_id"] =`                                              |
| 1433 | `          this.getAuthenticatedUser?.account_data_id \|\| "";`                    |
| 1437 | `        params["account_data_id"] =`                                              |
| 1438 | `          this.getAuthenticatedUser?.account_data_id \|\| "";`                    |
| 1439 | `        params["relational_entity_ids"] =`                                        |
| 1440 | `          this.componentData?.selected_relational_entity_ids;`                    |
| 1494 | `          type: "warning",`                                                       |
| 1647 | `        if (`                                                                     |
| 1648 | `          this.formbuilderDetails?.approval_receiver_permissions &&`              |
| 1649 | `          data.approval_status == "APPROVED"`                                     |
| 1650 | `        ) {`                                                                      |
| 1662 | `        } else if (`                                                              |
| 1663 | `          this.formbuilderDetails?.rejection_receiver_permissions &&`             |
| 1664 | `          data.approval_status == "REJECTED"`                                     |
| 1665 | `        ) {`                                                                      |
| 1835 | `        let params = this.getApprovalParams(`                                     |
| 1836 | `          formbuilderData,`                                                       |
| 1837 | `          currentuserIndex,`                                                      |
| 1838 | `          this.reasonForApprove`                                                  |
| 1839 | `        );`                                                                       |
| 1971 | `          this.getCompanyUsers = await postAPICall("GET", "/user/companyUsers");` |
| 1989 | `        this.getAllContacts = await postAPICall("GET", "/contacts", params);`     |

## src/components/customDashboard/customDashboardNotifications.vue

- Lines added: 4

| Line | Code                                                              |
| ---- | ----------------------------------------------------------------- |
| 259  | `            if (notification.customization) {`                   |
| 260  | `              query.customization = notification.customization;` |
| 285  | `            if (notification.customization) {`                   |
| 286  | `              query.customization = notification.customization;` |

## src/components/customDashboard/customDashboardStats.vue

- Lines added: 16

| Line | Code                                             |
| ---- | ------------------------------------------------ |
| 230  | `        show_full_title: false,`                |
| 876  | `          show_full_title: false,`              |
| 892  | `    deleteStatWithAI(component) {`              |
| 893  | `      this.$emit("deleteStat", component);`     |
| 1001 | `      this.addStatsData.icon = "dashboard";`    |
| 1002 | `      this.addStatsData.background_color = "";` |
| 1003 | `      this.addStatsData.font_color = "";`       |
| 1126 | `              ...{`                             |
| 1127 | `                isVisible: true,`               |
| 1128 | `                background_color: "#FFFFFF",`   |
| 1129 | `                show_full_title: false,`        |
| 1130 | `              },`                               |
| 1260 | `}`                                              |
| 1261 | `.custom-dashboard-top-buttons.auto-height {`    |
| 1262 | `  height: auto !important;`                     |
| 1263 | `}`                                              |

## src/components/customDashboard/customDashboardTable.vue

- Lines added: 32

| Line | Code                                                                        |
| ---- | --------------------------------------------------------------------------- |
| 1020 | `                                getFieldValue(scope.row, step, true)[0],`  |
| 1021 | `                                step`                                      |
| 2668 | `              keys.push(fd.id + "/values");`                               |
| 2765 | `      let customization = null;`                                           |
| 2766 | `      if (this.componentData?.selectedCustomizations?.relationalEntity) {` |
| 2767 | `        customization =`                                                   |
| 2768 | `          this.componentData.selectedCustomizations.relationalEntity;`     |
| 2769 | `      } else if (this.componentData?.selectedCustomizations?.entity) {`    |
| 2770 | `        customization = this.componentData.selectedCustomizations.entity;` |
| 2771 | `      } else if (`                                                         |
| 2772 | `        this.componentData?.selectedCustomizations?.nestedRelationEntity`  |
| 2773 | `      ) {`                                                                 |
| 2774 | `        customization =`                                                   |
| 2775 | `          this.componentData.selectedCustomizations.nestedRelationEntity;` |
| 2776 | `      } else if (this.componentData?.selectedCustomization) {`             |
| 2777 | `        customization = this.componentData.selectedCustomization;`         |
| 2778 | `      }`                                                                   |
| 2779 | `      if (customization) {`                                                |
| 2780 | `        addQuery["customization"] = customization;`                        |
| 2781 | `      }`                                                                   |
| 2973 | `          query: {`                                                        |
| 2974 | `            ...query,`                                                     |
| 2975 | `            ...{`                                                          |
| 2976 | `              layout: viewType,`                                           |
| 2977 | `              dashboardId: this.$route.params.dashboardId,`                |
| 2978 | `            },`                                                            |
| 2979 | `          },`                                                              |
| 3106 | `      if (searching) {`                                                    |
| 3525 | `          } else if (this.componentData?.selectedCustomization) {`         |
| 3526 | `            customization = this.componentData.selectedCustomization;`     |
| 3569 | `          } else if (this.componentData?.selectedCustomization) {`         |
| 3570 | `            customization = this.componentData.selectedCustomization;`     |

## src/components/customDashboard/schedulerComponent.vue

- Lines added: 5

| Line | Code                                                                                                                                       |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| 2    | `  <div v-loading="loading" class="custom-dashboard-scheduler" :class="{ 'mr-1 ml-1': getIsMobile }" :element-loading-text="loadingText">` |
| 224  | `                                } !important;`" @click="viewSchedulingData(item, day.day, day.month)">`                                   |
| 377  | `                            } !important;`" @click="viewSchedulingData(item, day.day, day.month)">`                                       |
| 1401 | `    async viewSchedulingData(item, day, month) {`                                                                                         |
| 1404 | `        month-1,`                                                                                                                         |

## src/components/employee/EmployeeDocuments.vue

- Lines added: 2

| Line | Code                                                                            |
| ---- | ------------------------------------------------------------------------------- |
| 238  | `        console.log("sendWorkflow", err);`                                     |
| 251  | `    this.$store.commit("users/setUserCompleteProfile", null, { root: true });` |

## src/components/employee/EmployeeProfile.vue

- Lines added: 3

| Line | Code                                                                            |
| ---- | ------------------------------------------------------------------------------- |
| 101  | ``                                                                              |
| 239  | `        console.log("sendWorkflow", err);`                                     |
| 253  | `    this.$store.commit("users/setUserCompleteProfile", null, { root: true });` |

## src/components/employee/PreviewTemplate.vue

- Lines added: 27

| Line | Code                                                                                              |
| ---- | ------------------------------------------------------------------------------------------------- |
| 3    | `    v-loading.fullscreen.lock="loading"`                                                         |
| 129  | `                :data="field"`                                                                   |
| 130  | `                v-if="field.input_type === 'AUTO_INCREMENT_NUMBER'"`                             |
| 131  | `                :form="form"`                                                                    |
| 132  | `                :is-view="!isExecute"`                                                           |
| 133  | `              ></AutoIncrementExecute>`                                                          |
| 134  | `              <StarRatingExecute`                                                                |
| 142  | `                v-if="field.input_type === 'CONCATENATE'"`                                       |
| 148  | `                v-if="field.input_type === 'RANDOM_TEXT'"`                                       |
| 154  | `                v-if="field.input_type === 'ADDRESS'"`                                           |
| 160  | `                v-if="field.input_type === 'PRICE'"`                                             |
| 166  | `                v-if="field.input_type === 'SLOT'"`                                              |
| 194  | `import RandomTextExecute from "../templates/formComponentsExecute/RandomTextExecute";`           |
| 195  | `import PriceCalculatorExecute from "../templates/formComponentsExecute/PriceCalculatorExecute";` |
| 196  | `import SlotsExecute from "../templates/formComponentsExecute/SlotsExecute";`                     |
| 215  | `    CheckBoxGroupExecute,`                                                                       |
| 551  | `        console.log("addNewWorkflowData", err);`                                                 |
| 736  | `    this.$store.commit("workflowData/setNewWorkflowData", null, { root: true });`                |
| 737  | `    this.$store.commit(`                                                                         |
| 738  | `      "workflowData/setWorkflowDataCreateByTemplateStatus",`                                     |
| 739  | `      null,`                                                                                     |
| 740  | `      { root: true }`                                                                            |
| 741  | `    );`                                                                                          |
| 742  | `    this.$store.commit("workflowData/setWorkflowTemplateDataAddStatus", null, {`                 |
| 743  | `      root: true,`                                                                               |
| 744  | `    });`                                                                                         |
| 745  | `  },`                                                                                            |

## src/components/employee/documentRequests/RequestedEmployeeDocuments.vue

- Lines added: 17

| Line | Code                                                                                                          |
| ---- | ------------------------------------------------------------------------------------------------------------- |
| 10   | `                  <img src="@/assets/img/template-icons/database-files.svg" alt="icon" class="img-fluid" />` |
| 20   | `            <data-tables-server v-loading="configureLoading" :fullscreen="true" :data="data" :total="total"` |
| 21   | `              :current-page.sync="currentPage" :page-size="pageSize" :pagination-props="paginationProps"`    |
| 22   | `              @query-change="loadData" style="width: 100%">`                                                 |
| 23   | `              <el-table-column label="Document Name" id="name" width="300" fixed="left">`                    |
| 26   | `                  }}</template>`                                                                             |
| 29   | `              <el-table-column v-if="!employeeId" label="Document Owner" id="employee" min-width="300">`     |
| 32   | `                  }}</template>`                                                                             |
| 38   | `                  }}</template>`                                                                             |
| 41   | `              <el-table-column prop="action" label="Action" fixed="right" width="150">`                      |
| 46   | `                        <img src="@/assets/img/icons/visibility.svg" alt="icon" />`                          |
| 66   | `<script>`                                                                                                    |
| 115  | `  created() { },`                                                                                            |
| 273  | `    this.$store.commit("employeeDocuments/setEmployeeDocumentsRequests", null, { root: true })`              |
| 274  | `    this.$store.commit("employeeDocuments/setDownloadUrl", null, { root: true })`                            |
| 275  | `    this.$store.commit("employeeDocuments/setDownloadError", null, { root: true })`                          |
| 276  | `    this.$store.commit("employeeDocuments/setDeleteDocumentError", null, { root: true })`                    |

## src/components/employeeDocuments/viewDocuments/DocumentPreview.vue

- Lines added: 9

| Line | Code                                                                                                   |
| ---- | ------------------------------------------------------------------------------------------------------ |
| 2113 | `        const today = new Date();`                                                                    |
| 2114 | `        const documentExpiredDate = new Date(`                                                        |
| 2115 | `          this.getDocumentPreviewData?.document_settings?.expiration_settings?.document_expired_date` |
| 2116 | `        );`                                                                                           |
| 2117 | `        if (today >= documentExpiredDate) {`                                                          |
| 2118 | `          this.isWorkflowExpired = true;`                                                             |
| 2119 | `        }`                                                                                            |
| 2120 | `        if(!this.isWorkflowExpired){`                                                                 |
| 2128 | `      }`                                                                                              |

## src/components/entity/AddEditEntity.vue

- Lines added: 116

| Line | Code                                                                               |
| ---- | ---------------------------------------------------------------------------------- |
| 1460 | `                    <div class="form-label">Select Entities</div>`                |
| 1462 | `                      v-model="roleEntities"`                                     |
| 1463 | `                      placeholder="Select Entities"`                              |
| 1467 | `                      multiple`                                                   |
| 1476 | `                        :key="entity._id + '_' + index"`                          |
| 1483 | `                  <!-- Role Name + Level per entity -->`                          |
| 1484 | `                  <template v-for="entityId in roleEntities">`                    |
| 1485 | `                    <!-- Primary Field -->`                                       |
| 1486 | `                    <template>`                                                   |
| 1487 | `                      <el-col`                                                    |
| 1488 | `                        :xs="24"`                                                 |
| 1489 | `                        :sm="12"`                                                 |
| 1490 | `                        :md="6"`                                                  |
| 1491 | `                        :key="entityId + '-name'"`                                |
| 1492 | `                      >`                                                          |
| 1493 | `                        <div class="form-label">`                                 |
| 1494 | `                          Select Primary Field in {{ getEntityName(entityId) }}`  |
| 1495 | `                        </div>`                                                   |
| 1496 | `                        <el-select`                                               |
| 1497 | `                          v-model="roleConfig[entityId].roleName"`                |
| 1498 | `                          :placeholder="`Select ${getEntityName(`                 |
| 1499 | `                            entityId`                                             |
| 1500 | `                          )} Name`"`                                              |
| 1501 | `                          size="mini"`                                            |
| 1502 | `                          clearable`                                              |
| 1503 | `                          filterable`                                             |
| 1504 | `                          style="width: 100%"`                                    |
| 1505 | `                        >`                                                        |
| 1506 | `                          <el-option`                                             |
| 1507 | `                            v-for="field in getEntityFields(entityId)"`           |
| 1508 | `                            :key="field.template_key"`                            |
| 1509 | `                            :label="field.label"`                                 |
| 1510 | `                            :value="field.template_key"`                          |
| 1511 | `                          />`                                                     |
| 1512 | `                        </el-select>`                                             |
| 1513 | `                      </el-col>`                                                  |
| 1514 | `                    </template>`                                                  |
| 1515 | ``                                                                                 |
| 1516 | `                    <!-- Level Field -->`                                         |
| 1517 | `                     <template>`                                                  |
| 1518 | `                      <el-col`                                                    |
| 1519 | `                        :xs="24"`                                                 |
| 1520 | `                        :sm="12"`                                                 |
| 1521 | `                        :md="6"`                                                  |
| 1522 | `                        :key="entityId + '-level'"`                               |
| 1523 | `                      >`                                                          |
| 1524 | `                      <div class="form-label">`                                   |
| 1525 | `                        Select Level from {{ getEntityName(entityId) }}`          |
| 1526 | `                      </div>`                                                     |
| 1527 | `                      <el-select`                                                 |
| 1528 | `                        v-model="roleConfig[entityId].roleLevel"`                 |
| 1529 | `                        :placeholder="`Select ${getEntityName(entityId)} Level`"` |
| 1530 | `                        size="mini"`                                              |
| 1531 | `                        clearable`                                                |
| 1532 | `                        filterable`                                               |
| 1533 | `                        style="width: 100%"`                                      |
| 1534 | `                      >`                                                          |
| 1535 | `                        <el-option`                                               |
| 1536 | `                          v-for="field in getEntityFields(entityId)"`             |
| 1537 | `                          :key="field.template_key"`                              |
| 1538 | `                          :label="field.label"`                                   |
| 1539 | `                          :value="field.template_key"`                            |
| 1540 | `                        />`                                                       |
| 1541 | `                      </el-select>`                                               |
| 1542 | `                    </el-col>`                                                    |
| 1543 | `                    </template>`                                                  |
| 1544 | `                  </template>`                                                    |
| 2395 | `      roleEntities: [],`                                                          |
| 2396 | `      roleConfig: {},`                                                            |
| 2397 | `      entityFieldsMap: {},`                                                       |
| 2543 | `    getEntityName(entityId) {`                                                    |
| 2544 | `      const entity = this.allEntitiesData.find((e) => e._id === entityId);`       |
| 2545 | `      return entity ? entity.name : "";`                                          |
| 2546 | `    },`                                                                           |
| 2547 | `    getEntityFields(entityId) {`                                                  |
| 2548 | `      return this.entityFieldsMap[entityId] \|\| [];`                             |
| 2549 | `    },`                                                                           |
| 2721 | `      this.$set(this.entityFieldsMap, entityId, this.selectedEntityFields);`      |
| 3200 | `        let roleDetails = [];`                                                    |
| 3201 | `        if (Array.isArray(this.getEntityDataById?.role_details)) {`               |
| 3202 | `          roleDetails = this.getEntityDataById.role_details;`                     |
| 3203 | `        } else if (`                                                              |
| 3204 | `          this.getEntityDataById?.role_details &&`                                |
| 3205 | `          typeof this.getEntityDataById.role_details === "object"`                |
| 3206 | `        ) {`                                                                      |
| 3207 | `          roleDetails = [this.getEntityDataById.role_details];`                   |
| 3208 | `        }`                                                                        |
| 3209 | `        if (this.login_mode === "rbac" && roleDetails.length) {`                  |
| 3210 | `          this.roleEntities = roleDetails.map((item) => item.roleEntity);`        |
| 3211 | `          roleDetails.forEach((item) => {`                                        |
| 3212 | `            this.$set(this.roleConfig, item.roleEntity, {`                        |
| 3213 | `              roleName: item.roleName,`                                           |
| 3214 | `              roleLevel: item.roleLevel,`                                         |
| 3215 | `            });`                                                                  |
| 3216 | `            this.fetchFieldsByEntity(item.roleEntity);`                           |
| 3217 | `          });`                                                                    |
| 3320 | `            : this.roleEntities.map((entityId) => ({`                             |
| 3321 | `                roleEntity: entityId,`                                            |
| 3322 | `                roleName: this.roleConfig[entityId]?.roleName \|\| null,`         |
| 3323 | `                roleLevel: this.roleConfig[entityId]?.roleLevel \|\| null,`       |
| 3324 | `              })),`                                                               |
| 4278 | `    roleEntities(newEntities) {`                                                  |
| 4279 | `      newEntities.forEach((id) => {`                                              |
| 4280 | `        if (!this.roleConfig[id]) {`                                              |
| 4281 | `          this.$set(this.roleConfig, id, { roleName: null, roleLevel: null });`   |
| 4282 | `        }`                                                                        |
| 4283 | `        if (!this.entityFieldsMap[id]) {`                                         |
| 4284 | `          this.fetchFieldsByEntity(id);`                                          |
| 4285 | `        }`                                                                        |
| 4286 | `      });`                                                                        |
| 4287 | `      Object.keys(this.roleConfig).forEach((id) => {`                             |
| 4288 | `        if (!newEntities.includes(id)) {`                                         |
| 4289 | `          this.$delete(this.roleConfig, id);`                                     |
| 4290 | `          this.$delete(this.entityFieldsMap, id);`                                |
| 4291 | `        }`                                                                        |
| 4292 | `      });`                                                                        |

## src/components/entity/EntityConditionalBlocks.vue

- Lines added: 1

| Line | Code                                                                       |
| ---- | -------------------------------------------------------------------------- |
| 764  | `                     <el-option value="=" label="Value (=)"></el-option>` |

## src/components/entity/EntityTemplateCustomization.vue

- Lines added: 5

| Line | Code                               |
| ---- | ---------------------------------- |
| 97   | `                      clearable`  |
| 142  | `                      clearable`  |
| 154  | `                      clearable`  |
| 422  | `        "AUTO_INCREMENT_NUMBER",` |
| 423  | `        "ADDRESS",`               |

## src/components/entity/FieldLevelPermissions.vue

- Lines added: 29

| Line | Code                                                                     |
| ---- | ------------------------------------------------------------------------ |
| 11   | `                    {{ scope.row.label }}`                              |
| 144  | `    <span`                                                              |
| 145  | `      slot="footer"`                                                    |
| 146  | `      class="dialog-footer mt-2 mb-1"`                                  |
| 147  | `      style="float: right; margin-right: 2%"`                           |
| 148  | `    >`                                                                  |
| 149  | `      <el-button @click="handleCancel()">Cancel</el-button>`            |
| 150  | `      <el-button type="primary" @click="handleSave()">Save</el-button>` |
| 233  | `      hiddenColumns: [`                                                 |
| 234  | `        "LABEL",`                                                       |
| 235  | `        "INPUT_TYPE",`                                                  |
| 236  | `        "FONT_SIZE",`                                                   |
| 237  | `        "FONT_COLOUR",`                                                 |
| 238  | `        "FONT_STYLE",`                                                  |
| 239  | `        "LABEL_ALIGNMENT",`                                             |
| 240  | `      ],`                                                               |
| 241  | `      originalCustomization: {},`                                       |
| 245  | `  props: ["templateData", "customization", "fromFormbuilder"],`         |
| 249  | `    this.originalCustomization = this.customization;`                   |
| 250  | `    if (this.templateData) {`                                           |
| 251  | `      this.fields = this.templateData;`                                 |
| 258  | `      return this.fieldProperties.filter(`                              |
| 259  | `        (col) => !this.hiddenColumns.includes(col.value)`               |
| 260  | `      );`                                                               |
| 261  | `    },`                                                                 |
| 267  | `      this.$emit("updateCustomization", this.customization);`           |
| 270  | `      this.customization = JSON.parse(`                                 |
| 271  | `        JSON.stringify(this.originalCustomization)`                     |
| 272  | `      );`                                                               |

## src/components/entity/RoleBasedAccessControlMenu.vue

- Lines added: 45

| Line | Code                                                                             |
| ---- | -------------------------------------------------------------------------------- |
| 1307 | `        let roleDetails = [];`                                                  |
| 1308 | `        if (Array.isArray(this.entityDetails?.role_details)) {`                 |
| 1309 | `          roleDetails = this.entityDetails.role_details;`                       |
| 1310 | `        } else if (`                                                            |
| 1311 | `          this.entityDetails?.role_details &&`                                  |
| 1312 | `          typeof this.entityDetails.role_details === "object"`                  |
| 1313 | `        ) {`                                                                    |
| 1314 | `          roleDetails = [this.entityDetails.role_details];`                     |
| 1315 | `        }`                                                                      |
| 1316 | `        for (const role of roleDetails) {`                                      |
| 1317 | `          const entity_id = role.roleEntity;`                                   |
| 1318 | `          const roleName = role.roleName;`                                      |
| 1319 | `          const roleLevel = role.roleLevel \|\| null; // optional`              |
| 1320 | `          const entityData = await this.fetchEntityData(entity_id, roleLevel);` |
| 1321 | `          const roles = await this.filterRolesData(`                            |
| 1322 | `            entityData,`                                                        |
| 1323 | `            roleName,`                                                          |
| 1324 | `            roleLevel`                                                          |
| 1325 | `          );`                                                                   |
| 1326 | `          this.allRoles.push(`                                                  |
| 1327 | `            ...roles.map((role) => ({`                                          |
| 1328 | `              ...role,`                                                         |
| 1329 | `              entityId: entity_id,`                                             |
| 1330 | `            }))`                                                                |
| 1331 | `          );`                                                                   |
| 1332 | `          this.selectedRole = this.allRoles[0]?._id \|\| "";`                   |
| 1333 | `          const selected = this.allRoles.find(`                                 |
| 1334 | `            (r) => r._id === this.selectedRole`                                 |
| 1335 | `          );`                                                                   |
| 1336 | `          this.selectedRoleName = selected ? selected.name : "";`               |
| 1337 | `        }`                                                                      |
| 1398 | `          sortBy: level ? level : undefined,`                                   |
| 1424 | `    async filterRolesData(data, roleName, roleLevel = null) {`                  |
| 1428 | `        let role_level = roleLevel ? roleLevel.split("#")[1] : null;`           |
| 1429 | `        return (`                                                               |
| 1430 | `          data?.map((item) => {`                                                |
| 1431 | `            const role = item.entityData[templateId];`                          |
| 1432 | `            return {`                                                           |
| 1433 | `              _id: item._id,`                                                   |
| 1434 | `              name: role[role_name],`                                           |
| 1435 | `              level: role_level ? role[role_level] : null,`                     |
| 1436 | `            };`                                                                 |
| 1437 | `          }) \|\| []`                                                           |
| 1438 | `        );`                                                                     |
| 1628 | `      this.getEntityMenu = this.getAllEntityMenus?.find(`                       |

## src/components/entity/ViewEntityData.vue

- Lines added: 155

| Line  | Code                                                                                 |
| ----- | ------------------------------------------------------------------------------------ |
| 408   | `                    ref="selectSearchSettings"`                                     |
| 409   | `                    @focus="closeOtherSelects('selectSearchSettings')"`             |
| 411   | ``                                                                                   |
| 497   | `                  ref="selectTableSettings"`                                        |
| 498   | `                  @focus="closeOtherSelects('selectTableSettings')"`                |
| 1110  | `                  v-if="`                                                           |
| 1111  | `                    !isApplicationUserSide &&`                                      |
| 1112  | `                    checkPerimission('SETTINGS') &&`                                |
| 1113  | `                    activeEntityView !== 'CARDS'`                                   |
| 1114  | `                  "`                                                                |
| 2133  | `                      <div`                                                         |
| 2134  | `                        v-else-if="`                                                |
| 2135  | `                          step &&`                                                  |
| 2136  | `                          ['MULTI_LINE_TEXT', 'ADDRESS'].includes(step.type)`       |
| 2137  | `                        "`                                                          |
| 2138  | `                      >`                                                            |
| 3820  | `                    <div`                                                           |
| 3821  | `                      v-else-if="`                                                  |
| 3822  | `                        step &&`                                                    |
| 3823  | `                        ['MULTI_LINE_TEXT', 'ADDRESS'].includes(step.type)`         |
| 3824  | `                      "`                                                            |
| 3825  | `                    >`                                                              |
| 4798  | `                <span class="group-value text-gray-600">`                           |
| 4799  | `                  {{ getOtherFieldValue(getSelectedFieldLabels[i]) }}`              |
| 4800  | `                </span>`                                                            |
| 4803  | `                <div`                                                               |
| 4804  | `                  v-show="!collapsedGroups[i]"`                                     |
| 4805  | `                  class="group-table"`                                              |
| 4806  | `                  v-loading="groupTablesLoading"`                                   |
| 4807  | `                  element-loading-text="Refreshing data..."`                        |
| 4808  | `                >`                                                                  |
| 5534  | `                              v-else-if="`                                          |
| 5535  | `                                step &&`                                            |
| 5536  | `                                ['MULTI_LINE_TEXT', 'ADDRESS'].includes(`           |
| 5537  | `                                  step.type`                                        |
| 5538  | `                                )`                                                  |
| 5539  | `                              "`                                                    |
| 6619  | `            <el-pagination`                                                         |
| 8367  | `                Action Button`                                                      |
| 8824  | `                <div`                                                               |
| 8825  | `                  v-if="`                                                           |
| 8826  | `                    selectedGroupbyField &&`                                        |
| 8827  | `                    selectedGroupbyField.input_type == 'ENTITY'`                    |
| 8828  | `                  "`                                                                |
| 8829  | `                >`                                                                  |
| 8830  | `                  Display other Field of this entity`                               |
| 8831  | `                  <el-select`                                                       |
| 9964  | `        showSavedFilters: false,`                                                   |
| 9980  | `        showSavedFilters: false,`                                                   |
| 10088 | `        selectedEntityOtherFields: [],`                                             |
| 10173 | `        { label: "Audit Logs", value: "Audit Logs" },`                              |
| 10233 | `      GroupbyEntityotherFields: [],`                                                |
| 11106 | `        "selectSearchSettings",`                                                    |
| 11144 | `          "selectSearchSettings",`                                                  |
| 13378 | `          is_restrict_users: field_info.restrict_users ? true : false,`             |
| 13379 | `          external_login: field_info.external_idp_login ? true : false,`            |
| 13380 | `          company_slug: this.getCompanyDetails.slug,`                               |
| 17924 | `        if (this.$route?.query?.filter === "") {`                                   |
| 17925 | `          let filter = this.UsercurrentFilter;`                                     |
| 17926 | `          this.fetchEntitiesDataForTable(filter?.filters \|\| []);`                 |
| 17927 | `        }`                                                                          |
| 18110 | `        showSavedFilters: this.entityFiltersData.showSavedFilters \|\| false,`      |
| 18281 | `            showSavedFilters: this.entityFiltersData?.showSavedFilters \|\| false,` |
| 20112 | `        this.GroupbyEntityotherFields = this.getEntityOtherFields(`                 |
| 20113 | `          this.quickentityData`                                                     |
| 20114 | `        );`                                                                         |
| 20117 | `    },`                                                                             |
| 20127 | `          template_fields_data: getAllFieldsArrayFromEntity(`                       |
| 20128 | `            this.quickentityData`                                                   |
| 20129 | `          ),`                                                                       |
| 20137 | `        let selectedEntityFields = await this.fetchEntityDetails(`                  |
| 20138 | `          this.quickentityData._id,`                                                |
| 20139 | `          true`                                                                     |
| 20140 | `        );`                                                                         |
| 20141 | `        let fieldsObject = {};`                                                     |
| 20142 | `        let entityFields = await this.fetchEntityDetails(`                          |
| 20143 | `          this.quickentityData._id,`                                                |
| 20144 | `          true`                                                                     |
| 20145 | `        );`                                                                         |
| 20146 | `        this.quickentityData?.primaryFields.map((e) => {`                           |
| 20147 | `          let field = selectedEntityFields.find(`                                   |
| 20148 | `            (fd) => fd.template_id == e.template_id && fd.key == e.key`             |
| 20150 | `          let key = e.key.includes("#") ? e.key : e.template_id + "#" + e.key;`     |
| 20151 | `          fieldsObject[key] = field;`                                               |
| 20152 | `        });`                                                                        |
| 20153 | `        entityFields.forEach((e) => {`                                              |
| 20154 | `          let key = e.key.includes("#") ? e.key : e.template_id + "#" + e.key;`     |
| 20155 | `          fieldsObject[key] = e;`                                                   |
| 20156 | `        });`                                                                        |
| 20157 | `        this.selectedEntityData = await this.dataParseWorker.formatDataForTable(`   |
| 20158 | `          {`                                                                        |
| 20159 | `            dataArray: this.selectedEntityData,`                                    |
| 20160 | `            columnList: entityFields.map((e) => {`                                  |
| 20161 | `              return {`                                                             |
| 20162 | `                template_id: e.template_id,`                                        |
| 20163 | `                key: e.key,`                                                        |
| 20164 | `              };`                                                                   |
| 20165 | `            }),`                                                                    |
| 20166 | `            fieldsObject: fieldsObject,`                                            |
| 20167 | `          }`                                                                        |
| 20168 | `        );`                                                                         |
| 20169 | `      }`                                                                            |
| 20170 | `      this.selectedDataIds = this.selectedEntityData.map(`                          |
| 20171 | `        (row, i) =>`                                                                |
| 20172 | `          row._id \|\| this.getEntityFieldLabel(row, this.quickentityData, i + 1)`  |
| 20175 | `        ...this.selectedDataIds,`                                                   |
| 20176 | `      ];`                                                                           |
| 20180 | `      let params = {`                                                               |
| 20181 | `        name: this.currentEntity.name,`                                             |
| 20182 | `        id: this.currentEntity._id,`                                                |
| 20183 | `        views_configuration: {`                                                     |
| 20184 | `          ...this.showFieldsParent,`                                                |
| 20185 | `        },`                                                                         |
| 20186 | `      };`                                                                           |
| 20213 | `      if (checked) {`                                                               |
| 20214 | `        this.GroupbyEntityotherFields = this.getEntityOtherFields(`                 |
| 20215 | `          this.quickentityData`                                                     |
| 20216 | `        );`                                                                         |
| 20217 | `      } else {`                                                                     |
| 20218 | `        this.GroupbyEntityotherFields = [];`                                        |
| 20219 | `        this.showFieldsParent.selectedEntityOtherFields = [];`                      |
| 20220 | `      }`                                                                            |
| 20226 | `        "IMAGE",`                                                                   |
| 20227 | `        "VIDEO",`                                                                   |
| 20236 | `        "ENTITY_TABLE",`                                                            |
| 20237 | `      ];`                                                                           |
| 20251 | `                return el;`                                                         |
| 20260 | `      if (`                                                                         |
| 20261 | `        !this.showFieldsParent.selectedEntityOtherFields \|\|`                      |
| 20262 | `        this.selectedGroupbyField?.input_type != "ENTITY"`                          |
| 20263 | `      )`                                                                            |
| 20264 | `        return "";`                                                                 |
| 20267 | `      const keys = Array.isArray(`                                                  |
| 20268 | `        this.showFieldsParent.selectedEntityOtherFields`                            |
| 20269 | `      )`                                                                            |
| 20270 | `        ? this.showFieldsParent.selectedEntityOtherFields`                          |
| 20271 | `        : [this.showFieldsParent.selectedEntityOtherFields];`                       |
| 20272 | `      const row = this.selectedEntityData.find((p) => {`                            |
| 20273 | `        return (`                                                                   |
| 20274 | `          this.showFieldsParent.groupbyEntityFieldSelectedOptions.includes(`        |
| 20275 | `            p.entity_data_id`                                                       |
| 20276 | `          ) && p[key] === op`                                                       |
| 20277 | `        );`                                                                         |
| 20278 | `      });`                                                                          |
| 20279 | `      if (!row) return "";`                                                         |
| 20280 | `      const selectedFields = keys`                                                  |
| 20281 | `        .map((k) => this.GroupbyEntityotherFields.find((f) => f.key === k))`        |
| 20282 | `        .filter(Boolean);`                                                          |
| 20283 | `      const values = selectedFields.map((field) => {`                               |
| 20287 | `      return values.join(", ");`                                                    |
| 20458 | `    "showFieldsParent.selectedEntityOtherFields": {`                                |
| 20459 | `      handler() {`                                                                  |
| 20460 | `        this.$forceUpdate();`                                                       |
| 20461 | `      },`                                                                           |
| 20462 | `      deep: true,`                                                                  |

## src/components/entity/entityFilters.vue

- Lines added: 27

| Line | Code                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------- |
| 13   | `        <div`                                                                                                      |
| 14   | `          class="try-ai-container mt-1 mr-1 d-flex align-items-center"`                                            |
| 15   | `          v-if="!fromConstApproverFilters"`                                                                        |
| 16   | `        >`                                                                                                         |
| 500  | `          <div`                                                                                                    |
| 501  | `            v-if="entityFiltersData.displayType === 'CARDS'"`                                                      |
| 502  | `            class="flex-column"`                                                                                   |
| 503  | `            style="margin-top: 25px"`                                                                              |
| 504  | `          >`                                                                                                       |
| 505  | `            <div class="flex items-center">`                                                                       |
| 506  | `              <el-checkbox v-model="entityFiltersData.showSavedFilters">`                                          |
| 507  | `                Display Saved Filters`                                                                             |
| 508  | `              </el-checkbox>`                                                                                      |
| 509  | ``                                                                                                                  |
| 510  | `              <el-popover`                                                                                         |
| 511  | `                trigger="hover"`                                                                                   |
| 512  | `                width="100%"`                                                                                      |
| 513  | `                placement="top"`                                                                                   |
| 514  | `                content="If checked, the saved filters card will be displayed. Otherwise, it will remain hidden."` |
| 515  | `              >`                                                                                                   |
| 516  | `                <i class="el-icon-info" slot="reference"></i>`                                                     |
| 517  | `              </el-popover>`                                                                                       |
| 518  | `            </div>`                                                                                                |
| 519  | `          </div>`                                                                                                  |
| 1520 | `    if (this.entityFiltersData.showSavedFilters === undefined) {`                                                  |
| 1521 | `      this.$set(this.entityFiltersData, "showSavedFilters", false);`                                               |
| 1522 | `    }`                                                                                                             |

## src/components/entity/externalEntityViewData.vue

- Lines added: 43

| Line | Code                                                                              |
| ---- | --------------------------------------------------------------------------------- |
| 837  | `        if (validEntityFields.length) {`                                         |
| 838  | `          await Promise.all(`                                                    |
| 839  | `            validEntityFields.map(async (field) => {`                            |
| 840  | `              const primaryDataValues = mappedData.map(`                         |
| 841  | `                (data) => data[field.template_key]`                              |
| 842  | `              );`                                                                |
| 843  | `              const params = {`                                                  |
| 844  | `                entity_id: field.entity_id,`                                     |
| 845  | `                limit: mappedData.length,`                                       |
| 846  | `                page: 1,`                                                        |
| 847  | `                filters: [`                                                      |
| 848  | `                  {`                                                             |
| 849  | `                    field: field.primary_fields[0],`                             |
| 850  | `                    operator: "in",`                                             |
| 851  | `                    value: primaryDataValues,`                                   |
| 852  | `                  },`                                                            |
| 853  | `                ],`                                                              |
| 854  | `                template_fields_data: [`                                         |
| 855  | `                  {`                                                             |
| 856  | `                    template_id: field.primary_fields[0].split("#")[0],`         |
| 857  | `                    fields: [field.primary_fields[0].split("#")[1]],`            |
| 858  | `                  },`                                                            |
| 859  | `                ],`                                                              |
| 861  | `                fields: [field.primary_fields[0]],`                              |
| 862  | `              };`                                                                |
| 863  | ``                                                                                |
| 864  | `              const result = await this.getEntityData(params);`                  |
| 865  | `              const validValues = new Set(`                                      |
| 866  | `                result.data.map(`                                                |
| 867  | `                  (item) => item.templates_fields_data[field.primary_fields[0]]` |
| 868  | `                )`                                                               |
| 869  | `              );`                                                                |
| 870  | `              this.tableData = [`                                                |
| 871  | `                ...this.tableData,`                                              |
| 872  | `                ...mappedData.filter((row) =>`                                   |
| 873  | `                  validValues.has(row[field.template_key])`                      |
| 874  | `                ),`                                                              |
| 875  | `              ];`                                                                |
| 876  | `            })`                                                                  |
| 877  | `          );`                                                                    |
| 878  | `        } else {`                                                                |
| 879  | `          this.tableData = [...this.tableData, ...mappedData];`                  |
| 880  | `        }`                                                                       |

## src/components/formBuilders/NewFormBuilder.vue

- Lines added: 170

| Line  | Code                                                                                                                                                                                                                   |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 282   | `                        v-if="`                                                                                                                                                                                       |
| 283   | `                          formBuilderId &&`                                                                                                                                                                           |
| 284   | `                          formBuilder.user_type &&`                                                                                                                                                                   |
| 285   | `                          formBuilder.user_type.length &&`                                                                                                                                                            |
| 286   | `                          formBuilder.allow_field_level_permissions`                                                                                                                                                  |
| 287   | `                        "`                                                                                                                                                                                            |
| 291   | `                          @click="`                                                                                                                                                                                   |
| 292   | `                            openFormBuilderSettings(`                                                                                                                                                                 |
| 293   | `                              formBuilder.form_builders_owner,`                                                                                                                                                       |
| 294   | `                              formBuilder.user_type`                                                                                                                                                                  |
| 295   | `                            )`                                                                                                                                                                                        |
| 296   | `                          "`                                                                                                                                                                                          |
| 308   | `                    <div`                                                                                                                                                                                             |
| 316   | `                      <el-select`                                                                                                                                                                                     |
| 317   | `                        placeholder="Select Entity"`                                                                                                                                                                  |
| 318   | `                        v-model="formBuilder.entity_id"`                                                                                                                                                              |
| 319   | `                        :filterable="true"`                                                                                                                                                                           |
| 320   | `                        :clearable="true"`                                                                                                                                                                            |
| 321   | `                        @change="setSettingsEntity"`                                                                                                                                                                  |
| 322   | `                        style="width: 300px"`                                                                                                                                                                         |
| 323   | `                      >`                                                                                                                                                                                              |
| 324   | `                        <el-option`                                                                                                                                                                                   |
| 325   | `                          v-for="(entity, index) of entitiesData.filter(`                                                                                                                                             |
| 326   | `                            (e) =>`                                                                                                                                                                                   |
| 327   | `                              (e.entity_type == 'INDIVIDUAL' \|\|`                                                                                                                                                    |
| 328   | `                                e.entity_type == 'BUSINESS') &&`                                                                                                                                                      |
| 329   | `                              e.type !== 'STANDARD'`                                                                                                                                                                  |
| 330   | `                          ) \|\| []"`                                                                                                                                                                                 |
| 331   | `                          :key="index"`                                                                                                                                                                               |
| 332   | `                          :label="entity.name"`                                                                                                                                                                       |
| 333   | `                          :value="entity._id"`                                                                                                                                                                        |
| 334   | `                        ></el-option>`                                                                                                                                                                                |
| 335   | `                      </el-select>`                                                                                                                                                                                   |
| 336   | `                      <el-tooltip`                                                                                                                                                                                    |
| 339   | `                        v-if="`                                                                                                                                                                                       |
| 340   | `                          formBuilderId &&`                                                                                                                                                                           |
| 341   | `                          formBuilder.entity_id &&`                                                                                                                                                                   |
| 342   | `                          formBuilder.allow_field_level_permissions`                                                                                                                                                  |
| 343   | `                        "`                                                                                                                                                                                            |
| 347   | `                          @click="`                                                                                                                                                                                   |
| 348   | `                            openFormBuilderSettings(`                                                                                                                                                                 |
| 349   | `                              formBuilder.form_builders_owner,`                                                                                                                                                       |
| 350   | `                              formBuilder.entity_id`                                                                                                                                                                  |
| 351   | `                            )`                                                                                                                                                                                        |
| 352   | `                          "`                                                                                                                                                                                          |
| 1837  | `                                allFormBuilderOriginalFields`                                                                                                                                                         |
| 1942  | `                                <el-col`                                                                                                                                                                              |
| 1943  | `                                  :span="2"`                                                                                                                                                                          |
| 1944  | `                                  v-if="`                                                                                                                                                                             |
| 1945  | `                                    formBuilder.allow_field_level_permissions`                                                                                                                                        |
| 1946  | `                                  "`                                                                                                                                                                                  |
| 1947  | `                                >`                                                                                                                                                                                    |
| 2235  | `                                <el-col`                                                                                                                                                                              |
| 2236  | `                                  :span="4"`                                                                                                                                                                          |
| 2237  | `                                  v-if="`                                                                                                                                                                             |
| 2238  | `                                    formBuilder.allow_field_level_permissions`                                                                                                                                        |
| 2239  | `                                  "`                                                                                                                                                                                  |
| 2240  | `                                >`                                                                                                                                                                                    |
| 2302  | `                                <el-col`                                                                                                                                                                              |
| 2303  | `                                  :span="2"`                                                                                                                                                                          |
| 2304  | `                                  v-if="`                                                                                                                                                                             |
| 2305  | `                                    formBuilder.allow_field_level_permissions`                                                                                                                                        |
| 2306  | `                                  "`                                                                                                                                                                                  |
| 2307  | `                                >`                                                                                                                                                                                    |
| 2588  | `                          <div class="mt-1">`                                                                                                                                                                         |
| 2589  | `                            <span style="font-weight: 500; font-size: 16px">`                                                                                                                                         |
| 2590  | `                              Field Level Permissions:`                                                                                                                                                               |
| 2591  | `                            </span>`                                                                                                                                                                                  |
| 2592  | `                            <br />`                                                                                                                                                                                   |
| 2593  | `                            <el-tooltip`                                                                                                                                                                              |
| 2594  | `                              class="item"`                                                                                                                                                                           |
| 2595  | `                              effect="dark"`                                                                                                                                                                          |
| 2596  | `                              content="If enabled, you can set field-level permissions for approvers and fillers. You can make fields required, read-only, or hidden when the form is being filled out or approved."` |
| 2597  | `                              placement="top"`                                                                                                                                                                        |
| 2598  | `                            >`                                                                                                                                                                                        |
| 2599  | `                              <el-checkbox`                                                                                                                                                                           |
| 2600  | `                                v-model="`                                                                                                                                                                            |
| 2601  | `                                  formBuilder.allow_field_level_permissions`                                                                                                                                          |
| 2602  | `                                "`                                                                                                                                                                                    |
| 2603  | `                                class="mt-1 mb-1"`                                                                                                                                                                    |
| 2604  | `                                :disabled="`                                                                                                                                                                          |
| 2605  | `                                  !formBuilder \|\| !formBuilder.steps?.length`                                                                                                                                       |
| 2606  | `                                "`                                                                                                                                                                                    |
| 2607  | `                                @change="onFieldLevelPermissionChange"`                                                                                                                                               |
| 2608  | `                              >`                                                                                                                                                                                      |
| 2609  | `                                Allow Field Level Permissions`                                                                                                                                                        |
| 2610  | `                              </el-checkbox>`                                                                                                                                                                         |
| 2611  | `                            </el-tooltip>`                                                                                                                                                                            |
| 2612  | `                          </div>`                                                                                                                                                                                     |
| 2613  | `                          <br />`                                                                                                                                                                                     |
| 5116  | `                              <el-col`                                                                                                                                                                                |
| 5117  | `                                :span="2"`                                                                                                                                                                            |
| 5118  | `                                v-if="formBuilder.allow_field_level_permissions"`                                                                                                                                     |
| 5119  | `                              >`                                                                                                                                                                                      |
| 5212  | `                              <el-col`                                                                                                                                                                                |
| 5213  | `                                :span="2"`                                                                                                                                                                            |
| 5214  | `                                v-if="formBuilder.allow_field_level_permissions"`                                                                                                                                     |
| 5215  | `                              >`                                                                                                                                                                                      |
| 7411  | `        allow_field_level_permissions: false,`                                                                                                                                                                        |
| 7953  | `        "INTEGRATION",`                                                                                                                                                                                               |
| 7954  | `        "INTEGRATION_VARIABLE",`                                                                                                                                                                                      |
| 7955  | `        "PRICE",`                                                                                                                                                                                                     |
| 7956  | `        "SLOT",`                                                                                                                                                                                                      |
| 8960  | `    async getAllFormBuilderFieldsOriginal(types) {`                                                                                                                                                                   |
| 8962  | `      if (!this.formBuilder \|\| !this.formBuilder.steps) return allFields;`                                                                                                                                          |
| 8963  | `      for (const [index, step] of this.formBuilder.steps.entries()) {`                                                                                                                                                |
| 8964  | `        if (step.type === "ENTITY" && step.entity) {`                                                                                                                                                                 |
| 8965  | `          const matchedEntity = await fetchEntityById(step.entity);`                                                                                                                                                  |
| 8966  | `          if (matchedEntity?.templates?.length) {`                                                                                                                                                                    |
| 8967  | `            for (const t of matchedEntity.templates) {`                                                                                                                                                               |
| 8968  | `              const customization = t?.customization \|\| {};`                                                                                                                                                        |
| 8969  | `              const fields = t.templateInfo?.sections[0]?.fields \|\| [];`                                                                                                                                            |
| 8970  | ``                                                                                                                                                                                                                     |
| 8971  | `              const customizedFields = await this.applyCustomizationOnFields(`                                                                                                                                        |
| 8972  | `                fields,`                                                                                                                                                                                              |
| 8973  | `                customization`                                                                                                                                                                                        |
| 8974  | `              );`                                                                                                                                                                                                     |
| 8975  | `              const primaryFields = matchedEntity?.primaryFields \|\| [];`                                                                                                                                            |
| 8976  | `              customizedFields.forEach((fl) => {`                                                                                                                                                                     |
| 8978  | `                  const isPrimary = primaryFields.some(`                                                                                                                                                              |
| 8979  | `                    (pf) => pf.key === fl.key`                                                                                                                                                                        |
| 8980  | `                  );`                                                                                                                                                                                                 |
| 8983  | `                   key:`${index}#${t.template_id}#${fl.key}`,`                                                                                                                                                        |
| 8984  | `                    isPrimary: !!isPrimary,`                                                                                                                                                                          |
| 8990  | `        } else if (step.type === "TEMPLATE" && step.template) {`                                                                                                                                                      |
| 8991  | `          const currentTemplate = (this.allTemplatesData \|\| []).find(`                                                                                                                                              |
| 8992  | `            (e) => e._id === step.template`                                                                                                                                                                           |
| 8993  | `          );`                                                                                                                                                                                                         |
| 8994  | `          if (!currentTemplate?.sections?.[0]) continue;`                                                                                                                                                             |
| 8995  | ``                                                                                                                                                                                                                     |
| 8996  | `          const fields = currentTemplate.sections[0].fields \|\| [];`                                                                                                                                                 |
| 8997  | `          fields.forEach((fl) => {`                                                                                                                                                                                   |
| 8998  | `            if (types?.includes(fl.inputType)) {`                                                                                                                                                                     |
| 8999  | `              allFields.push({`                                                                                                                                                                                       |
| 9000  | `                ...fl,`                                                                                                                                                                                               |
| 9001  | `               key:`${index}#${currentTemplate.\_id}#${fl.key}`,`                                                                                                                                                     |
| 9002  | `              });`                                                                                                                                                                                                    |
| 9003  | `            }`                                                                                                                                                                                                        |
| 9004  | `          });`                                                                                                                                                                                                        |
| 9005  | `        }`                                                                                                                                                                                                            |
| 9009  | `    async onFieldLevelPermissionChange(value) {`                                                                                                                                                                      |
| 9010  | `      if (value) {`                                                                                                                                                                                                   |
| 9011  | `        this.allFormBuilderOriginalFields =`                                                                                                                                                                          |
| 9012  | `          await this.getAllFormBuilderFieldsOriginal(this.types);`                                                                                                                                                    |
| 9013  | `      } else {`                                                                                                                                                                                                       |
| 9014  | `        this.allFormBuilderOriginalFields = [];`                                                                                                                                                                      |
| 9015  | `      }`                                                                                                                                                                                                              |
| 9016  | `    },`                                                                                                                                                                                                               |
| 10460 | `        this.formBuilder.allow_field_level_permissions =`                                                                                                                                                             |
| 10461 | `          data.allow_field_level_permissions;`                                                                                                                                                                        |
| 10577 | `        if (data.allow_field_level_permissions) {`                                                                                                                                                                    |
| 10578 | `          this.allFormBuilderOriginalFields =`                                                                                                                                                                        |
| 10579 | `            await this.getAllFormBuilderFieldsOriginal(this.types);`                                                                                                                                                  |
| 10580 | `        }`                                                                                                                                                                                                            |
| 11554 | `          } else if (user === "ENTITY") {`                                                                                                                                                                            |
| 11555 | `            userIdentifier = user;`                                                                                                                                                                                   |
| 11556 | `          } else if (user === "USER") {`                                                                                                                                                                              |
| 11557 | `            userIdentifier = user;`                                                                                                                                                                                   |
| 11563 | `            } else if (userIdentifier === "USER" && Array.isArray(index)) {`                                                                                                                                          |
| 11564 | `             this.selectedUserAndFilter =`${userIdentifier}#${index.join(`                                                                                                                                            |
| 11565 | `                "#"`                                                                                                                                                                                                  |
| 11566 | `              )}`;`                                                                                                                                                                                                   |
| 11664 | `    async "formBuilder.steps"(newVal) {`                                                                                                                                                                              |
| 11665 | `      if (newVal && newVal.length) {`                                                                                                                                                                                 |
| 11666 | `        const allFields = await this.getAllFormBuilderFieldsOriginal(`                                                                                                                                                |
| 11667 | `          this.types`                                                                                                                                                                                                 |
| 11668 | `        );`                                                                                                                                                                                                           |
| 11669 | `        this.allFormBuilderOriginalFields = allFields;`                                                                                                                                                               |
| 11670 | `      }`                                                                                                                                                                                                              |
| 11671 | `    },`                                                                                                                                                                                                               |

## src/components/formBuilders/advancedApprovalDataActions.vue

- Lines added: 17

| Line | Code                                                                                               |
| ---- | -------------------------------------------------------------------------------------------------- |
| 284  | `          >`                                                                                      |
| 285  | `            <span class="actions-label">Repeat Type</span>`                                       |
| 286  | `            <el-select`                                                                           |
| 287  | `              v-model="action.repeat_type"`                                                       |
| 288  | `              clearable`                                                                          |
| 289  | `              filterable`                                                                         |
| 290  | `              size="mini"`                                                                        |
| 291  | `              class="actions-input"`                                                              |
| 292  | `            >`                                                                                    |
| 293  | `              <el-option label="One Time Per User" value="one_time_per_user" />`                  |
| 294  | `              <el-option label="Every Time" value="every_time" />`                                |
| 295  | `            </el-select>`                                                                         |
| 296  | `          </div>`                                                                                 |
| 297  | `          <div`                                                                                   |
| 298  | `            class="actions-field"`                                                                |
| 299  | `            v-if="action.action_type == 'trigger_form_builder' && action.trigger_formbuilder_id"` |
| 1097 | `        isRepeat: true,`                                                                          |

## src/components/formBuilders/advancedApprovalSettings.vue

- Lines added: 90

| Line | Code                                                                                                                          |
| ---- | ----------------------------------------------------------------------------------------------------------------------------- |
| 77   | `            <el-tooltip content="Field Level Permissions" placement="top" v-if="formBuilder.allow_field_level_permissions">` |
| 160  | `              <el-option`                                                                                                    |
| 161  | `                v-for="(advUser) in previousLevelsProfileApprovers"`                                                         |
| 162  | `                :key="advUser.value"`                                                                                        |
| 163  | `                :label="advUser.label"`                                                                                      |
| 164  | `                :value="advUser.value"`                                                                                      |
| 165  | `              ></el-option>`                                                                                                 |
| 431  | `          <template v-else-if="user.user_type == 'USER_PROFILE'">`                                                           |
| 432  | `            <el-col :span="6">`                                                                                              |
| 433  | `              <el-select`                                                                                                    |
| 434  | `                v-model="user.user_profile_field"`                                                                           |
| 435  | `                clearable`                                                                                                   |
| 436  | `                size="mini"`                                                                                                 |
| 437  | `                placeholder="Select a field from the user profile"`                                                          |
| 438  | `                class="ml-1"`                                                                                                |
| 439  | `              >`                                                                                                             |
| 440  | `                <el-option`                                                                                                  |
| 441  | `                  v-for="(option, index) of userProfileFields"`                                                              |
| 442  | `                  :key="index"`                                                                                              |
| 443  | `                  :value="option.key"`                                                                                       |
| 444  | `                  :label="option.label"`                                                                                     |
| 445  | `                  >{{ option.label }}</el-option`                                                                            |
| 446  | `                >`                                                                                                           |
| 447  | `              </el-select>`                                                                                                  |
| 448  | `            </el-col>`                                                                                                       |
| 449  | `          </template>`                                                                                                       |
| 450  | `          <template v-else-if="user.user_type.includes('related-to#levelIndex')">`                                           |
| 451  | `            <el-col :span="6">`                                                                                              |
| 452  | `              <el-select`                                                                                                    |
| 453  | `                v-model="user.user_profile_field"`                                                                           |
| 454  | `                clearable`                                                                                                   |
| 455  | `                size="mini"`                                                                                                 |
| 456  | `                placeholder="Select a field"`                                                                                |
| 457  | `                class="ml-1"`                                                                                                |
| 458  | `              >`                                                                                                             |
| 459  | `                <el-option`                                                                                                  |
| 460  | `                  v-for="(option, index) of userProfileFields"`                                                              |
| 461  | `                  :key="index"`                                                                                              |
| 462  | `                  :value="option.key"`                                                                                       |
| 463  | `                  :label="option.label"`                                                                                     |
| 464  | `                  >{{ option.label }}</el-option`                                                                            |
| 465  | `                >`                                                                                                           |
| 466  | `              </el-select>`                                                                                                  |
| 467  | `            </el-col>`                                                                                                       |
| 468  | `          </template>`                                                                                                       |
| 658  | `      userProfileFields: [],`                                                                                                |
| 677  | `        { value: "USER_PROFILE", label: "Related to User Profile (Filling User Profile)" },`                                 |
| 718  | `  async mounted() {`                                                                                                         |
| 719  | `    await this.getFillingUserProfileFields();`                                                                               |
| 722  | `    async getFillingUserProfileFields() {`                                                                                   |
| 723  | `      let fields = [];`                                                                                                      |
| 724  | `      if (this.formBuilder.form_builders_owner == "ENTITY" && this.formBuilder?.entity_id) {`                                |
| 725  | `        fields = await this.getEntityFields(this.formBuilder.entity_id);`                                                    |
| 726  | `        fields = fields`                                                                                                     |
| 727  | `          .filter(f => f.input_type === "ENTITY")`                                                                           |
| 728  | `          .map(f => ({`                                                                                                      |
| 729  | `            ...f,`                                                                                                           |
| 730  | `           key:`${f.entity_id}#${f.key}`,`                                                                                   |
| 731  | `          }));`                                                                                                              |
| 732  | `        this.userProfileFields = fields;`                                                                                    |
| 733  | `      }`                                                                                                                     |
| 734  | `    },`                                                                                                                      |
| 735  | `    getLevelProfileRelatedApprovers() {`                                                                                     |
| 736  | `      let profileApprovers = [];`                                                                                            |
| 737  | `      this.formBuilder.advanced_approval_users.forEach((app, index) => {`                                                    |
| 738  | `        if (app.role === "user" && index !== 0) {`                                                                           |
| 739  | `          profileApprovers.push({`                                                                                           |
| 740  | `           label:`Related to Level-${index + 1} user profile`,`                                                              |
| 741  | `           value:`related-to#levelIndex-${index}`,`                                                                          |
| 742  | `          });`                                                                                                               |
| 743  | `        } else if (`                                                                                                         |
| 744  | `          app.role === "approver" &&`                                                                                        |
| 745  | `          app.approver_type === "constant_approver" &&`                                                                      |
| 746  | `          app?.constant_approvers?.length`                                                                                   |
| 747  | `        ) {`                                                                                                                 |
| 748  | `          let findProfileApprover = app.constant_approvers.find(`                                                            |
| 749  | `            (e) => e.user_type === "USER_PROFILE" && e?.user_profile_field && this.currentLevelIndex !== index`              |
| 750  | `          );`                                                                                                                |
| 751  | ``                                                                                                                            |
| 752  | `          if (findProfileApprover) {`                                                                                        |
| 753  | `            profileApprovers.push({`                                                                                         |
| 754  | `             label:`Related to Level-${index + 1} Approver`,`                                                                |
| 755  | `             value:`related-to#levelIndex-${index}`,`                                                                        |
| 756  | `            });`                                                                                                             |
| 757  | `          }`                                                                                                                 |
| 758  | `        }`                                                                                                                   |
| 759  | `      });`                                                                                                                   |
| 760  | `      this.previousLevelsProfileApprovers = profileApprovers;`                                                               |
| 761  | `    },`                                                                                                                      |
| 915  | `        this.getLevelProfileRelatedApprovers();`                                                                             |

## src/components/formBuilders/approvalAuthReviewPage.vue

- Lines added: 1

| Line | Code                                                                                                                |
| ---- | ------------------------------------------------------------------------------------------------------------------- |
| 77   | `                from_rework: this.$route.query.from_rework \|\| this.$route.fullPath.includes("from_rework=true")` |

## src/components/formBuilders/formBuilderNewView.vue

- Lines added: 6

| Line | Code                           |
| ---- | ------------------------------ |
| 1060 | `  .fullscreen {`              |
| 1061 | `    height: 92vh !important;` |
| 1062 | `  }`                          |
| 1073 | `  .fullscreen {`              |
| 1074 | `    height: 92vh !important;` |
| 1075 | `  }`                          |

## src/components/formBuilders/formbuilderTemplatePreview.vue

- Lines added: 2

| Line | Code                                                               |
| ---- | ------------------------------------------------------------------ |
| 4094 | `          this.isApprovalForm &&`                                 |
| 4095 | `          this.formbuilderDetails?.allow_field_level_permissions` |

## src/components/payment/checkout.js

- Lines added: 10

| Line | Code                                                                                                              |
| ---- | ----------------------------------------------------------------------------------------------------------------- |
| 1    | `/* global Stripe */`                                                                                             |
| 3    | `// @ts-ignore - Stripe is loaded via https://js.stripe.com/v3/`                                                  |
| 4    | `const stripe = Stripe(`                                                                                          |
| 5    | `  "pk_test_51KqczISEKgdIVMl0FzLh7Ag73ieiFIQhzl7CNuRikhGVLUKqRgBGk50ZI7ibCUPo41mCWyakELAGyJFb4PmgfkJz00JkwQW2Yv"` |
| 6    | `);`                                                                                                              |
| 19   | `var emailAddress = "";`                                                                                          |
| 30   | `    theme: "stripe",`                                                                                            |
| 37   | `  linkAuthenticationElement.on("change", (event) => {`                                                           |
| 88   | `  console.log("paymentIntent", paymentIntent);`                                                                  |
| 132  | `}`                                                                                                               |

## src/components/templates/NewTemplate.vue

- Lines added: 3

| Line | Code                                                              |
| ---- | ----------------------------------------------------------------- |
| 5391 | `              field.options?.length == "0" &&`                   |
| 5393 | `            (field.options?.some((opt) => opt.trim() === "") &&` |
| 6625 | `        external_idp_login : false,`                             |

## src/components/templates/fields.json

- Lines added: 2

| Line | Code                      |
| ---- | ------------------------- |
| 1934 | `      "height": 100,`    |
| 1954 | `      "min_height": 80,` |

## src/components/templates/formComponents/AISettings.vue

- Lines added: 10

| Line | Code                                                                |
| ---- | ------------------------------------------------------------------- |
| 76   | `              v-for="(option, index) in supportedFields"`          |
| 174  | `      supportedFields: [],`                                        |
| 178  | `  mounted() {`                                                     |
| 179  | `    if (this.fieldData?.ai_settings?.isAIEnabled) {`               |
| 180  | `      const transformedFields = this.getFilteredAdditionalFields(` |
| 181  | `        this.fieldsData`                                           |
| 182  | `      );`                                                          |
| 183  | `      this.supportedFields = transformedFields;`                   |
| 184  | `    }`                                                             |
| 185  | `  },`                                                              |

## src/components/templates/formComponents/Address.vue

- Lines added: 5

| Line | Code                                                             |
| ---- | ---------------------------------------------------------------- |
| 100  | `        this.field.address?.enabled_subfields?.includes(f.key)` |
| 104  | `  created() {`                                                  |
| 109  | `    if(!this.field.address) {`                                  |
| 110  | `      this.$set(this.field, "address", {});`                    |
| 111  | `    }`                                                          |

## src/components/templates/formComponents/EntityAdvanced.vue

- Lines added: 74

| Line | Code                                                                      |
| ---- | ------------------------------------------------------------------------- |
| 63   | `          <el-checkbox`                                                  |
| 64   | `            v-model="field.detailed_view"`                               |
| 65   | `            @click="handleDetailedViewCheckbox"`                         |
| 66   | `          >`                                                             |
| 70   | `        <el-select`                                                      |
| 71   | `          class="ml-4"`                                                  |
| 72   | `          size="mini"`                                                   |
| 73   | `          multiple`                                                      |
| 74   | `          collapse-tags`                                                 |
| 75   | `          clearable`                                                     |
| 76   | `          v-if="field.detailed_view"`                                    |
| 77   | `          v-model="field.detailed_view_selected_fields"`                 |
| 78   | `          placeholder="Select Fields to show in detailed view"`          |
| 79   | `        >`                                                               |
| 80   | `          <el-option`                                                    |
| 81   | `            v-for="option in allEntityFields"`                           |
| 82   | `            :key="option.key"`                                           |
| 83   | `            :label="option.template_name + ' - ' + option.label"`        |
| 84   | `            :value="option.key"`                                         |
| 85   | `          />`                                                            |
| 86   | `        </el-select>`                                                    |
| 87   | `        <span class="select-fields" v-if="field.detailed_view">`         |
| 88   | `          <div style="margin-bottom: 10px">`                             |
| 89   | `            Select fields to use as quick filters`                       |
| 90   | `          </div>`                                                        |
| 91   | `          <el-select`                                                    |
| 92   | `            v-model="field.quick_filters"`                               |
| 93   | `            multiple`                                                    |
| 94   | `            placeholder="Select fields"`                                 |
| 95   | `            size="mini"`                                                 |
| 96   | `            collapse-tags`                                               |
| 97   | `            clearable`                                                   |
| 98   | `          >`                                                             |
| 99   | `            <el-option`                                                  |
| 100  | `              v-for="(field, index) of getQuickFilterFilters"`           |
| 101  | `              :key="index + '_' + field.key"`                            |
| 102  | `              :value="field.key"`                                        |
| 103  | `              :label="`${field.template_name} - ${field.label}`"`        |
| 104  | `             >{{`${field.template_name} - ${field.label}` }}</el-option` |
| 105  | `            >`                                                           |
| 106  | `          </el-select>`                                                  |
| 107  | `        </span>`                                                         |
| 129  | `      <el-col v-if="field && field.properties">`                         |
| 130  | `        <el-checkbox v-model="field.properties.hideValue">`              |
| 131  | `          Hide value`                                                    |
| 132  | `        </el-checkbox>`                                                  |
| 133  | `      </el-col>`                                                         |
| 418  | `          <el-option`                                                    |
| 419  | `            v-for="(option, index) in getGroupByOptions"`                |
| 420  | `            :key="index"`                                                |
| 421  | `            :value="option.template_id + '#' + option.key"`              |
| 422  | `            :label="option.label"`                                       |
| 423  | `          >`                                                             |
| 424  | `          </el-option>`                                                  |
| 473  | `    getQuickFilterFilters() {`                                           |
| 474  | `      const allowedTypes = [`                                            |
| 475  | `        "SELECT",`                                                       |
| 476  | `        "ENTITY",`                                                       |
| 477  | `        "MULTI_SELECT",`                                                 |
| 478  | `        "DATE",`                                                         |
| 479  | `        "DATE_TIME",`                                                    |
| 480  | `      ];`                                                                |
| 481  | `      return this.allEntityFields.filter((e) =>`                         |
| 482  | `        allowedTypes.includes(e.inputType \|\| e.input_type)`            |
| 483  | `      );`                                                                |
| 484  | `    },`                                                                  |
| 551  | `    handleDetailedViewCheckbox() {`                                      |
| 552  | `      if (`                                                              |
| 553  | `        this.field.detailed_view &&`                                     |
| 554  | `        !this.field.detailed_view_selected_fields`                       |
| 555  | `      ) {`                                                               |
| 556  | `        this.$set(this.field, "detailed_view_selected_fields", []);`     |
| 557  | `      }`                                                                 |
| 558  | `    },`                                                                  |

## src/components/templates/formComponents/File.vue

- Lines added: 15

| Line | Code                                                                                                                                              |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 102  | `              v-if="!field.validations.multiple"`                                                                                                |
| 114  | `              v-if="!field.validations.multiple"`                                                                                                |
| 116  | `                content="When selected, the copied link will be secured. The generated link is accessible only to users within this workspace."` |
| 120  | `              &nbsp; &nbsp;`                                                                                                                     |
| 121  | `              <span v-if="!field.validations.multiple && field.restrict_users"`                                                                  |
| 122  | `                ><el-checkbox v-model="field.external_idp_login"`                                                                                |
| 123  | `                  >External Idp Login</el-checkbox`                                                                                              |
| 124  | `                >`                                                                                                                               |
| 125  | `                <el-tooltip`                                                                                                                     |
| 126  | `                  effect="dark"`                                                                                                                 |
| 127  | `                  content="When selected, the secured copy link can only be accessed via the configured IdP login."`                             |
| 128  | `                >`                                                                                                                               |
| 129  | `                  <i class="el-icon-info"></i> </el-tooltip`                                                                                     |
| 130  | `              ></span>`                                                                                                                          |
| 131  | ``                                                                                                                                                |

## src/components/templates/formComponentsExecute/AddressExecute.vue

- Lines added: 3

| Line | Code                    |
| ---- | ----------------------- |
| 315  | `  padding: 3px;`       |
| 327  | `  max-height: 65px;`   |
| 331  | `  padding-right: 2px;` |

## src/components/templates/formComponentsExecute/SelectExecute.vue

- Lines added: 1

| Line | Code                                                                                                      |
| ---- | --------------------------------------------------------------------------------------------------------- |
| 96   | `      <el-row align="middle" v-else class="topfield" :class="{ 'topfield-sty': data.newlyAddedField }">` |

## src/components/templates/formComponentsExecute/SlotsExecute.vue

- Lines added: 25

| Line | Code                                                                                 |
| ---- | ------------------------------------------------------------------------------------ |
| 252  | `      let disabled = this.bookedSlots \|\| [];`                                     |
| 254  | `      if (this.checkIsDisabled && this.selectedSlot) {`                             |
| 255  | `        disabled = this.computedTimeSlots`                                          |
| 256  | `          .map((slot) => slot.start)`                                               |
| 257  | `          .filter((start) => start !== this.selectedSlot);`                         |
| 258  | `      }`                                                                            |
| 259  | `      const now = new Date();`                                                      |
| 260  | `      const selectedDate = new Date(this.selectedDate);`                            |
| 261  | `      const isToday = selectedDate.toDateString() === now.toDateString();`          |
| 262  | `      if (isToday) {`                                                               |
| 263  | `        const expiredSlots = this.computedTimeSlots`                                |
| 264  | `          .map((slot) => slot.start)`                                               |
| 265  | `          .filter((slot) => {`                                                      |
| 266  | `            const [hour, minute] = slot.split(":").map(Number);`                    |
| 267  | `            const slotDate = new Date();`                                           |
| 268  | `            slotDate.setHours(hour, minute, 0, 0);`                                 |
| 269  | `            return slotDate.getTime() < now.getTime();`                             |
| 270  | `          });`                                                                      |
| 272  | `        disabled = [...new Set([...disabled, ...expiredSlots])];`                   |
| 273  | `      }`                                                                            |
| 274  | `      return disabled;`                                                             |
| 395  | `    async selectSlot(slot) {`                                                       |
| 398  | `      await this.getEntityDataByFilter();`                                          |
| 399  | `      await this.checkAvailableSlots();`                                            |
| 411  | `      if (this.isFromFormBuilder \|\| this.entityData?.isCreatedFromFormbuilder) {` |

## src/components/templates/formComponentsExecute/TryUsingAI.vue

- Lines added: 6

| Line | Code                                                                             |
| ---- | -------------------------------------------------------------------------------- |
| 70   | `            v-for="(option, index) in supportedFields"`                         |
| 204  | `  mounted() {`                                                                  |
| 205  | `    let transformedFields = this.getFilteredAdditionalFields(this.fieldsData);` |
| 206  | `    this.supportedFields = transformedFields;`                                  |
| 207  | `  },`                                                                           |
| 237  | `      supportedFields: [],`                                                     |

## src/components/templates/previewFormbuilderTemplate.vue

- Lines added: 2

| Line | Code                                                                                                                  |
| ---- | --------------------------------------------------------------------------------------------------------------------- |
| 1341 | `        (this.$route.name === "FormbuilderEditStep" \|\| this.$route.name === "ApplicationUserFormbuilderEditStep")` |
| 1349 | `          this.formbuilderData?.logs,`                                                                               |

## src/components/widgets/EntityCalendarWidgets.vue

- Lines added: 1

| Line | Code                          |
| ---- | ----------------------------- |
| 1957 | `@media (max-width: 426px) {` |
