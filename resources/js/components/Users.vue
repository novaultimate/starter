<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">Tabel User</h3>
                        <div class="card-tools">
                            <button class="btn btn-success" data-toggle="modal" data-target="#addNewCenter">Tambah User <i class="fas fa-user-plus fa-fw"></i></button>
                        </div>
                    </div>

              <!-- /.card-header -->
              <div class="card-body table-responsive p-0">
                <table class="table table-hover">
                  <thead>
                    <tr>
                      <th>ID</th>
                      <th>Nama</th>
                      <th>Email</th>
                      <th>Tipe</th>
                      <th>Aksi</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td>183</td>
                      <td>John Doe</td>
                      <td>11-7-2014</td>
                      <td><span class="tag tag-success">Approved</span></td>
                      <td><a href="#"><i class="fa fa-edit"></i></a> | <a href="#"><i class="fa fa-trash red"></i></a></td>
                    </tr>
                    
                  </tbody>
                </table>
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
        </div>

   <!-- Modal -->
<div class="modal fade" id="addNewCenter" tabindex="-1" role="dialog" aria-labelledby="addNewLabel" aria-hidden="true">
  <div class="modal-dialog modal-dialog-centered" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="addNewLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <form @submit.prevent="createUser">
      <div class="modal-body">
        <div class="form-group">
      <input v-model="form.name" type="text" name="name" placeholder="Nama"
        class="form-control" :class="{ 'is-invalid': form.errors.has('name') }">
      <has-error :form="form" field="name"></has-error>
    </div>
        <div class="form-group">
      <input v-model="form.email" type="text" name="email" placeholder="Email"
        class="form-control" :class="{ 'is-invalid': form.errors.has('email') }">
      <has-error :form="form" field="email"></has-error>
    </div>
        <div class="form-group">
      <textarea v-model="form.bio" name="bio" id="bio" placeholder="Bio singkat"
        class="form-control" :class="{ 'is-invalid': form.errors.has('name') }"></textarea>
      <has-error :form="form" field="bio"></has-error>
    </div>
        <div class="form-group">
      <select v-model="form.type" name="type" id="type"
        class="form-control" :class="{ 'is-invalid': form.errors.has('type') }">
        <option value="">Pilih Tipe</option>
        <option value="admin">Admin</option>
        <option value="user">User</option>
        <option value="author">Author</option>
      </select>
      <has-error :form="form" field="type"></has-error>
    </div>
          <div class="form-group">
      <input v-model="form.password" type="password" name="password" id="password"
        class="form-control" :class="{ 'is-invalid': form.errors.has('password') }">
      <has-error :form="form" field="password"></has-error>
    </div>

      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" data-dismiss="modal">Tutup</button>
        <button type="submit" class="btn btn-primary">Tambah</button>
      </div>
      </form>
    </div>
  </div>
</div>
                    </div>
          
</template>

<script>
    export default {
        data(){
            return{
                form: new Form({
                    name: '',
                    email: '',
                    password: '',
                    type: '',
                    bio: '', 
                    photo: ''
                })
            }
        },
        methods: {
          createUser(){
            this.form.post('api/user');
          }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
