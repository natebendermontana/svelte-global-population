  <!-- buncha code just to get a glow to apply to the svg globe -->
  <defs>
    <filter id="glow" height="130%">
      <feGaussianBlur in="SourceAlpha" stdDeviation="25" />
      <feOffset dx="0" dy="0" result="offsetblur" />
      <feFlood flood-color="rgba(100,255,100, .65)" />
      <feComposite in2="offsetblur" operator="in" />
      <feMerge>
        <feMergeNode />
        <feMergeNode in="SourceGraphic" />
      </feMerge>
    </filter>
  </defs>