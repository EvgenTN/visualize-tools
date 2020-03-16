<template>
  <div class="shapes">
    <svg viewBox="0 0 105 250">
      <rect class="rect" x="10" y="10" width="30" height="30" />
      <rect class="rect" x="60" y="10" width="30" height="30" rx="10" ry="10" />
      <circle cx="25" cy="75" r="20" />
      <ellipse cx="75" cy="75" rx="20" ry="10" />
      <line x1="10" y1="110" x2="50" y2="150" />
      <polyline points="60 110 65 120 70 115 75 130 80 125 85 140 90 " />
      <polygon points="50 160 55 180 70 180 60 190 65 205 50 195 35 205" />
      <path d="M20,230 Q40,205 50,230 T90,230" />
    </svg>
  </div>
</template>

<script>
export default {
  name: "SvgShapes"
}
</script>