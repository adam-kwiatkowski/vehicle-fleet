<template>
  <div class="row">
    <div class="col-auto">
      <div class="input-group">
        <select
          class="form-select"
          id="size-select"
          @input="$emit('page-size', $event.target.value)"
        >
          <option selected>10</option>
          <option>25</option>
          <option>50</option>
          <option>100</option>
        </select>
        <label class="input-group-text" for="size-select">Per page</label>
      </div>
    </div>
    <div class="col align-self-end">
      <nav>
        <ul class="pagination justify-content-end">
          <li class="page-item" :class="{ disabled: current_page == 1 }">
            <a
              class="page-link"
              href="#"
              @click="$emit('change-page', current_page - 1)"
              >Previous</a
            >
          </li>
          <li class="page-item disabled">
            <a class="page-link" href="#"
              >{{ current_page }} of {{ last_page }}</a
            >
          </li>
          <li
            class="page-item"
            :class="{ disabled: current_page == last_page }"
          >
            <a
              class="page-link"
              href="#"
              @click="$emit('change-page', current_page + 1)"
              >Next</a
            >
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  props: ["current_page", "last_page"],
};
</script>