<script>
  import { onMount } from "svelte";
  export let vehiculo = {};

  const options = {
    year: "numeric",
    month: "short",
    day: "numeric",
  };

  let stringFechaMatriculacion = "void";

  if (vehiculo.fechaMatriculacion !== undefined) {
    const fechaMatriculacion = new Date(vehiculo.fechaMatriculacion);
    stringFechaMatriculacion = fechaMatriculacion.toLocaleDateString(
      "en-US",
      options
    );
  }
</script>

<div class="card border-secondary shadow">
  <div class="card-body">
    <div class="input-group mb-3">
      <span class="input-group-text" id="license">License plate</span>
      <input
        type="text"
        class="form-control"
        aria-label="License"
        aria-describedby="license"
        bind:value={vehiculo.matricula}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="brand">Brand</span>
      <input
        type="text"
        class="form-control"
        aria-label="Brand"
        aria-describedby="brand"
        bind:value={vehiculo.marca}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="model">Model</span>
      <input
        type="text"
        class="form-control"
        aria-label="Model"
        aria-describedby="model"
        bind:value={vehiculo.modelo}
      />
    </div>

    <div class="input-group mb-3">
      <span class="input-group-text" id="registration">Registration</span>
      <span class="input-group-text" id="textRegistration">
        {vehiculo.fechaMatriculacion !== undefined
          ? stringFechaMatriculacion
          : "Insert below"}
      </span>
    </div>

    <div class="input-group mb-3">
      <input
        type="date"
        class="form-control"
        aria-label="Registration"
        aria-describedby="registration"
        bind:value={vehiculo.fechaMatriculacion}
      />
    </div>

    <slot />
  </div>
</div>
