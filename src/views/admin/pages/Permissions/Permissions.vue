<template>
  <div class="permissons fluid-container mx-5" v-if="currentAccount?.permissions.includes('permissions')">
    <div class="is-fetching" v-if="!isFetching">
      <div class="permissons-title mt-4 d-flex align-items-center">
        <h4 class="gray-text">Permission Settings</h4>
        <h5 class="mx-1">/</h5> 
        <h4 class="primary-text">Permissions</h4>
      </div>
      <div class="row">
        <div class="mb-3 d-flex justify-content-end">
          <button
            type="submit"
            class="btn btn-main"
            @click="handleUpdate"
          >
            Update
          </button>
        </div>
      </div>
      <v-table fixed-header height="500px">
        <thead>
          <tr>
            <th class="text-left">
              Permissions\Role
            </th>
            <th class="text-center" v-for="role in roles">
              {{ role.title }}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th colspan="12">Products</th>
          </tr>
          <tr>
            <td>-- Create</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='create_products'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Read</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='read_products'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Update</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='update_products'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Delete</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='delete_products'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>

          <tr>
            <th colspan="12">Categories</th>
          </tr>
          <tr>
            <td>-- Create</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='create_product-categories'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Read</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='read_product-categories'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Update</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='update_product-categories'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Delete</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='delete_product-categories'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>

          <tr>
            <th colspan="12">Accounts</th>
          </tr>
          <tr>
            <td>-- Create</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='create_accounts'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Read</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='read_accounts'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Update</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='update_accounts'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Delete</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='delete_accounts'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>

          <tr>
            <th colspan="12">Roles</th>
          </tr>
          <tr>
            <td>-- Create</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='create_roles'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Read</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='read_roles'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Update</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='update_roles'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
          <tr>
            <td>-- Delete</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='delete_roles'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>

          <tr>
            <th colspan="12">Permissions</th>
          </tr>
          <tr>
            <td>-- Modify Permissons</td>
            <td class="text-center" v-for="role in roles">
              <v-checkbox
                v-model="role.permissions"
                value='permissions'
                hide-details
                color="primary"
                class="d-inline-flex"
              ></v-checkbox>
            </td>
          </tr>
        </tbody>
      </v-table>
    </div>
    <div class="is-fetching" v-else>
      <v-row>
        <v-col cols="6">
          <v-skeleton-loader
            color="grey-lighten-5"
            class="my-2"
            max-width="400"
            type="heading"
          ></v-skeleton-loader>
        </v-col>
      </v-row>
      <v-skeleton-loader
        color="grey-lighten-5"
        class="my-0"
        type="table-tbody"
      ></v-skeleton-loader>
    </div>
  </div>
  <div class="role fluid-container mx-5" v-else>
    <Unauthorized />
  </div>
</template>

<script>
  import { mapState } from 'pinia'
  import { useAuthStore } from '@/stores/admin/auth.store'
  import roleService from '@/services/admin/role.service'
  import successDialogHelper from '@/helpers/admin/dialogs/success.helper'
  import Unauthorized from '@/components/admin/Unauthorized/Unauthorized.vue'

  export default {
    components: {
      Unauthorized
    },
    data() {
      return {
        isFetching: true,
        roles: null
      }
    },
    methods: {
      async getRoles() {
        try {
          const result = await roleService.getAll()
          this.isFetching = false
          // limit field to reduce watching expense
          this.roles = result.roles.map(item => {
            return {
              _id: item._id,
              title: item.title,
              permissions: item.permissions,
              changed: false
            }
          })
        }
        catch (err) {
          console.log(err)
        }
      },
      async handleUpdate() {
        try {
          const data = this.roles.filter(role => role.changed === true)
          console.log(data)
          await roleService.updatePermission({ roles: data })
          successDialogHelper(
            "Updated!",
            "Permissions have been updated"
          )
        }
        catch (err) {
          console.log(err)
        }
      },
      handleChange(newVal) {
        newVal.changed = true
      }
    },
    async created() {
      await this.getRoles(),
      this.roles.forEach((val) => {
        this.$watch(() => val, this.handleChange, {deep: true});
      });
    },
    computed: {
      ...mapState(useAuthStore, ['currentAccount'])
    }
  }
</script>

<style scoped lang="scss">
</style>
