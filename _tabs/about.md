---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

### Hi there!

I'm Rrmeazh, an undergraduate from School of Engineering Mechanics, Norea University of Science & Technology (NUST). I'm planning to pursue a master degree at Department of Electronic Engineering or Greater Bay International Graduate School, NUST.

### About this site

<!-- Website Runtime Display -->
<div id="site-runtime-container" style="width:100%; 
        display:block;
        margin-bottom:1rem;
        background:inherit; 
        color:inherit;">
  <span id="site_runtime"></span>
</div>

<!-- running time calculation -->
<script>
  /* 
   * Set the website creation date in UTC format
   * This date should be when the site was first deployed
   */
  const siteCreateDate = new Date("2026-07-06T06:00:00Z");
  
  /*
   * Calculates and updates the website running time
   * This calculation is based purely on time differences (milliseconds)
   * It does not depend on calendar months/years, so it automatically
   * handles leap years, varying month lengths, daylight saving time changes, etc.
   */
  function updateRuntime() {
    const now = new Date();
    /* 
     * Calculate the difference in milliseconds
     * This is the most accurate method as it avoids calendar complexities
     */
    const diffMs = now - siteCreateDate;
    
    /* Calculate seconds (1 second = 1000 ms) */
    const totalSeconds = Math.floor(diffMs / 1000);
    const seconds = totalSeconds % 60;
    
    /* Calculate minutes (1 minute = 60 seconds) */
    const totalMinutes = Math.floor(totalSeconds / 60);
    const minutes = totalMinutes % 60;
    
    /* Calculate hours (1 hour = 60 minutes) */
    const totalHours = Math.floor(totalMinutes / 60);
    const hours = totalHours % 24;
    
    /* Calculate days (1 day = 24 hours) */
    const totalDays = Math.floor(totalHours / 24);
    
    /* Update the display */
    document.getElementById("site_runtime").textContent = 
      `This site has been running for ${totalDays} days ${hours} hours ${minutes} minutes ${seconds} seconds.`;
  }
  
  /* 
   * Initialize the timer:
   * 1. Update immediately when the page loads
   * 2. Set up an interval to update every second
   */
  updateRuntime();
  setInterval(updateRuntime, 1000);
</script>

Total posts published: {{ site.posts | size }}.
