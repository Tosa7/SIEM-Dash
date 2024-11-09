<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creating My First SIEM Dashboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            max-width: 800px;
            margin: auto;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        img {
            display: block;
            margin: 20px auto;
            width: 80%;
            height: auto;
        }
        code {
            background-color: #f4f4f4;
            padding: 2px 4px;
            border-radius: 4px;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border-radius: 4px;
            overflow-x: auto;
        }
    </style>
</head>
<body>

<h1>Creating My First SIEM Dashboard: A Journey Through Data Visualization</h1>

<h2>Description</h2>
<p>In my continuous pursuit to deepen my cybersecurity expertise, I recently tackled a project on creating a SIEM (Security Information and Event Management) dashboard, focusing on visualizing failed logon attempts. This project was part of my training with Hack The Box Academy, where I explored real-world scenarios and honed my practical skills in SIEM configuration.</p>

<h2>Utilities Used</h2>
<ul>
    <li><b>Kibana</b></li>
    <li><b>Elastic Stack</b></li>
    <li><b>KQL</b></li>
</ul>

<h2>Environments Used</h2>
<ul>
    <li><b>Windows Server</b></li>
    <li><b>Elastic Stack</b></li>
</ul>

<h2>Program Walk-Through:</h2>

<h3>1. Setting Up the Environment</h3>
<p>I started by navigating to the target system and accessing the dashboard interface at <code>http://[Target IP]:5601</code>.</p>
<img src="https://imgur.com/T0Dsy9w.png" alt="Dashboard Interface">
<p>Initially, I deleted any pre-existing dashboards (like "SOC-Alerts") to create a fresh workspace.</p>

<h3>2. Creating the Dashboard</h3>
<p>I clicked on the "Create new dashboard" button, which opened a clean slate for building visualizations.</p>

<h3>3. Configuring the First Visualization</h3>
<p>I initiated the visualization creation by selecting the "Create visualization" option and specified Event ID <code>4625</code> (indicating failed logon attempts on Windows systems) using the filter option.</p>
<img src="https://imgur.com/1594qyG.png" alt="Filter Configuration">
<p>The index pattern was set to <code>windows*</code>, ensuring data capture from Windows-based logs.</p>

<h3>4. Refining Data Selection</h3>
<p>I verified the existence of necessary fields, such as <code>user.name.keyword</code>, for accurate data aggregation.</p>
<img src="https://imgur.com/eCfCCjb.png" alt="Search Bar Verification">
<p>The "Table" type was chosen for visualization, and rows were configured to display usernames, the host machine, and the count of failed attempts.</p>

<h3>5. Adjusting Metrics and Settings</h3>
<p>Under "Metrics," I selected "Count" as the metric to populate the table with data.</p>
<img src="https://i.imgur.com/ZT4zr3u.png" alt="Metrics Configuration">
<p>An additional row was set to display <code>host.hostname.keyword</code>, detailing the involved machines.</p>

<h3>6. Incorporating Advanced Refinements</h3>
<p>To ensure relevance, I applied a KQL query to exclude computer accounts and specific system-generated usernames:</p>
<pre><code>NOT user.name: *$ AND winlog.channel.keyword: Security</code></pre>
<img src="https://i.imgur.com/gFqTKT8.png" alt="Advanced Filters with KQL">
<p>This refinement kept the data user-focused and excluded non-essential entries.</p>

<h3>7. Finalizing the Visualization</h3>
<p>I saved and titled the visualization, resulting in an informative table displaying usernames, host machines, and counts of failed logon attempts.</p>
<img src="https://i.imgur.com/1mSGYWv.png" alt="Completed Visualization">

<h2>Key Takeaways</h2>
<p>This project enhanced my practical understanding of building SIEM dashboards. It demonstrated:</p>
<ul>
    <li>The value of using filters to target specific data.</li>
    <li>Best practices for presenting data for SOC teams to identify threats.</li>
    <li>How to apply operational feedback, like excluding system accounts, for clearer visualizations.</li>
</ul>
<p>Completing this exercise prepared me for real-world SOC scenarios and improved my technical and analytical skills.</p>

<hr>
<p><i>This post documents my approach to learning and applying SIEM fundamentals, inspired by coursework from Hack The Box Academy.</i></p>

</body>
</html>
