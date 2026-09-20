<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BrokerBridge</title>
<meta name="description" content="BrokerBridge — A digital workspace connecting insurance brokers with insurance institutions.">

<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{--green:#173f32;--green2:#235c49;--gold:#c7a35a;--cream:#f6f4ee;--white:#fff;--text:#18231e;--muted:#718078;--border:#e5e9e6;--success:#2f8054;--warning:#b9862f;--danger:#b34c4c}
body{font-family:Inter,Arial,sans-serif;background:var(--cream);color:var(--text)}
button,input,select{font:inherit}button{cursor:pointer}
.login-screen{min-height:100vh;display:flex;align-items:center;justify-content:center;background:var(--green);padding:24px}
.login-box{width:100%;max-width:410px}.logo{text-align:center;color:#fff;margin-bottom:28px}
.logo-symbol,.sidebar-logo-symbol{background:var(--gold);color:var(--green);display:flex;align-items:center;justify-content:center;font-weight:800}
.logo-symbol{width:58px;height:58px;margin:0 auto 13px;border-radius:15px;font-size:20px}
.logo h1{font-size:29px}.logo p{margin-top:4px;color:#ffffffad;font-size:13px}
.login-card{background:#fff;border-radius:16px;padding:32px;box-shadow:0 25px 70px #0003}
.login-card h2{font-size:22px;margin-bottom:6px}.login-card>p{color:var(--muted);font-size:13px;margin-bottom:24px}
.form-group{margin-bottom:17px}label{display:block;font-size:12px;font-weight:700;margin-bottom:7px}
input,select{width:100%;border:1px solid var(--border);background:#fff;border-radius:8px;padding:11px 13px;outline:none;color:var(--text)}
input:focus,select:focus{border-color:var(--green2)}
.login-button,.primary{border:0;background:var(--green);color:#fff;font-weight:700}
.login-button{width:100%;border-radius:8px;padding:12px;margin-top:5px}.login-button:hover,.primary:hover{background:var(--green2)}
.login-footer{text-align:center;margin-top:18px;font-size:11px;color:var(--muted)}
.app{display:none;min-height:100vh}.sidebar{position:fixed;left:0;top:0;bottom:0;width:238px;background:var(--green);color:#fff;padding:20px 14px;z-index:100}
.sidebar-logo{display:flex;align-items:center;gap:10px;padding:5px 10px 27px}.sidebar-logo-symbol{width:38px;height:38px;border-radius:10px;font-size:13px}.sidebar-logo strong{font-size:18px}
.nav-title{font-size:9px;letter-spacing:1.2px;text-transform:uppercase;color:#ffffff6b;padding:0 11px;margin:17px 0 7px}
.nav-item{width:100%;border:0;background:transparent;color:#ffffffb8;padding:10px 11px;text-align:left;border-radius:7px;margin-bottom:2px;font-size:12px}.nav-item:hover,.nav-item.active{background:#ffffff1a;color:#fff}.nav-item span{display:inline-block;width:27px;opacity:.8}
.user-panel{position:absolute;bottom:17px;left:14px;right:14px;background:#ffffff12;border-radius:9px;padding:11px}.user-panel strong{display:block;font-size:12px}.user-panel small{font-size:10px;color:#ffffff8c}
.main{margin-left:238px;min-height:100vh}.topbar{height:68px;background:#fff;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;padding:0 28px;position:sticky;top:0;z-index:50}
.search{width:270px}.top-right{display:flex;align-items:center;gap:18px}.notification{position:relative;font-size:17px}.notification-dot{position:absolute;width:6px;height:6px;background:var(--danger);border-radius:50%;top:0;right:-2px}
.logout{border:1px solid var(--border);background:#fff;border-radius:7px;padding:7px 11px;font-size:11px}.mobile-menu{display:none;border:0;background:none;font-size:21px}
.content{padding:28px}.page{display:none}.page.active{display:block}.page-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:23px}
.page-header h1{font-size:25px;letter-spacing:-.4px}.page-header p{font-size:12px;color:var(--muted);margin-top:3px}.primary{padding:10px 15px;border-radius:7px;font-size:11px}
.kpis{display:grid;grid-template-columns:repeat(5,1fr);gap:14px;margin-bottom:20px}.kpi{background:#fff;border:1px solid var(--border);border-radius:11px;padding:17px}.kpi-label{color:var(--muted);font-size:10px}.kpi-value{font-size:25px;font-weight:800;margin:5px 0}.kpi-meta{font-size:9px}.green{color:var(--success)}.orange{color:var(--warning)}.red{color:var(--danger)}
.grid-2{display:grid;grid-template-columns:2fr 1fr;gap:18px;margin-bottom:18px}.card{background:#fff;border:1px solid var(--border);border-radius:11px;padding:19px}.card-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:17px}.card-header h3{font-size:13px}.card-header a{color:var(--green2);font-size:10px;cursor:pointer}
.chart{height:205px;display:flex;align-items:flex-end;gap:14px;padding:10px 5px 0;border-bottom:1px solid var(--border)}.bar-group{flex:1;height:100%;display:flex;flex-direction:column;justify-content:flex-end;align-items:center}.bar{width:48%;min-height:8px;background:var(--green);border-radius:5px 5px 0 0}.bar-label{font-size:9px;color:var(--muted);margin-top:7px}
.activity{display:flex;gap:10px;padding:11px 0;border-bottom:1px solid var(--border)}.activity:last-child{border-bottom:0}.activity-icon{width:29px;height:29px;border-radius:50%;background:#edf2ee;color:var(--green);display:flex;align-items:center;justify-content:center;font-size:11px;flex-shrink:0}.activity strong{font-size:11px}.activity div{font-size:10px}.activity-time{color:var(--muted);margin-top:2px}
.table-card{background:#fff;border:1px solid var(--border);border-radius:11px;overflow:hidden}.toolbar{display:flex;justify-content:space-between;align-items:center;padding:15px 18px;border-bottom:1px solid var(--border)}.toolbar h3{font-size:13px}.toolbar input{width:220px;padding:8px 10px;font-size:11px}.table-wrapper{overflow-x:auto}
table{width:100%;border-collapse:collapse;min-width:720px}th,td{padding:13px 17px;text-align:left;border-bottom:1px solid var(--border);font-size:10px}th{background:#fafbfa;color:var(--muted);font-size:9px;text-transform:uppercase;letter-spacing:.4px}td strong{font-size:11px}
.status{display:inline-block;padding:4px 8px;border-radius:20px;font-size:8px;font-weight:700}.status.green{background:#e5f3e9;color:#287147}.status.yellow{background:#fff3d9;color:#94691d}.status.red{background:#fae4e4;color:#a33f3f}.status.blue{background:#e7eff5;color:#416b88}
.action{border:1px solid var(--border);background:#fff;border-radius:6px;padding:5px 8px;font-size:9px}
.institutions,.products,.resources{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}.institution,.product,.resource{background:#fff;border:1px solid var(--border);border-radius:11px;padding:18px}.institution-logo{width:43px;height:43px;background:#edf2ee;color:var(--green);border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;margin-bottom:13px}
.institution h3,.product h3,.resource h3{font-size:13px;margin-bottom:5px}.institution p,.product p,.resource p{color:var(--muted);font-size:10px;margin-bottom:12px}.tags{margin-bottom:13px}.tag{display:inline-block;background:#f1f3f1;padding:4px 7px;border-radius:20px;font-size:8px;margin:2px}
.task{background:#fff;border:1px solid var(--border);border-radius:9px;padding:14px;display:flex;align-items:center;gap:12px;margin-bottom:9px}.task-check{width:19px;height:19px;border:2px solid var(--border);border-radius:5px}.task-info{flex:1}.task-info strong{display:block;font-size:11px}.task-info small{font-size:9px;color:var(--muted)}
.settings-card{max-width:700px}.settings-card h3{font-size:14px;margin-bottom:20px}
@media(max-width:1100px){.kpis{grid-template-columns:repeat(3,1fr)}.institutions,.products,.resources{grid-template-columns:repeat(2,1fr)}}
@media(max-width:800px){.sidebar{transform:translateX(-100%);transition:.25s}.sidebar.open{transform:translateX(0)}.main{margin-left:0}.mobile-menu{display:block}.search{display:none}.grid-2{grid-template-columns:1fr}.kpis{grid-template-columns:repeat(2,1fr)}.content{padding:20px}}
@media(max-width:520px){.kpis{grid-template-columns:1fr}.institutions,.products,.resources{grid-template-columns:1fr}.page-header{align-items:flex-start;flex-direction:column;gap:12px}.topbar{padding:0 18px}.login-card{padding:25px}}
</style>
</head>

<body>

<section class="login-screen" id="loginScreen">
<div class="login-box">
<div class="logo">
<div class="logo-symbol">BB</div>
<h1>BrokerBridge</h1>
<p>Connecting Brokers. Simplifying Insurance.</p>
</div>

<div class="login-card">
<h2>Welcome back</h2>
<p>Sign in to your broker workspace.</p>

<form id="loginForm">
<div class="form-group">
<label for="email">Email Address</label>
<input id="email" type="email" placeholder="Enter your email" required>
</div>

<div class="form-group">
<label for="password">Password</label>
<input id="password" type="password" placeholder="Enter your password" required>
</div>

<button class="login-button" type="submit">Sign In</button>
</form>

<div class="login-footer">Secure broker workspace</div>
</div>
</div>
</section>

<section class="app" id="app">

<aside class="sidebar" id="sidebar">
<div class="sidebar-logo">
<div class="sidebar-logo-symbol">BB</div>
<strong>BrokerBridge</strong>
</div>

<div class="nav-title">Workspace</div>
<button class="nav-item active" data-page="dashboard"><span>▦</span>Dashboard</button>
<button class="nav-item" data-page="clients"><span>♙</span>Clients</button>
<button class="nav-item" data-page="applications"><span>▤</span>Quotes & Applications</button>

<div class="nav-title">Insurance</div>
<button class="nav-item" data-page="institutions"><span>◈</span>Institutions</button>
<button class="nav-item" data-page="products"><span>◇</span>Products</button>

<div class="nav-title">Management</div>
<button class="nav-item" data-page="documents"><span>▧</span>Documents</button>
<button class="nav-item" data-page="tasks"><span>✓</span>Tasks</button>
<button class="nav-item" data-page="reports"><span>▥</span>Reports</button>

<div class="nav-title">Resources</div>
<button class="nav-item" data-page="resources"><span>◉</span>Resources</button>
<button class="nav-item" data-page="settings"><span>⚙</span>Settings</button>
<button class="nav-item" data-page="support"><span>?</span>Help & Support</button>

<div class="user-panel">
<strong>Broker Account</strong>
<small>Independent Broker</small>
</div>
</aside>

<main class="main">
<header class="topbar">
<button class="mobile-menu" id="mobileMenu">☰</button>
<input class="search" type="search" placeholder="Search BrokerBridge...">
<div class="top-right">
<div class="notification">🔔<span class="notification-dot"></span></div>
<button class="logout" onclick="logout()">Logout</button>
</div>
</header>

<div class="content">

<section class="page active" id="dashboard">
<div class="page-header">
<div><h1>Dashboard</h1><p>Overview of your brokerage activity.</p></div>
<button class="primary" onclick="showPage('clients')">+ Add Client</button>
</div>

<div class="kpis">
<div class="kpi"><div class="kpi-label">Active Clients</div><div class="kpi-value">128</div><div class="kpi-meta green">↑ 8.2% this month</div></div>
<div class="kpi"><div class="kpi-label">Open Applications</div><div class="kpi-value">24</div><div class="kpi-meta green">↑ 4 this week</div></div>
<div class="kpi"><div class="kpi-label">Pending Quotes</div><div class="kpi-value">11</div><div class="kpi-meta orange">5 require action</div></div>
<div class="kpi"><div class="kpi-label">Completed</div><div class="kpi-value">76</div><div class="kpi-meta green">↑ 12.4%</div></div>
<div class="kpi"><div class="kpi-label">Tasks Due</div><div class="kpi-value">7</div><div class="kpi-meta red">2 overdue</div></div>
</div>

<div class="grid-2">
<div class="card">
<div class="card-header"><h3>Applications Overview</h3><a>Last 6 months</a></div>
<div class="chart">
<div class="bar-group"><div class="bar" style="height:40%"></div><div class="bar-label">Apr</div></div>
<div class="bar-group"><div class="bar" style="height:55%"></div><div class="bar-label">May</div></div>
<div class="bar-group"><div class="bar" style="height:48%"></div><div class="bar-label">Jun</div></div>
<div class="bar-group"><div class="bar" style="height:70%"></div><div class="bar-label">Jul</div></div>
<div class="bar-group"><div class="bar" style="height:63%"></div><div class="bar-label">Aug</div></div>
<div class="bar-group"><div class="bar" style="height:85%"></div><div class="bar-label">Sep</div></div>
</div>
</div>

<div class="card">
<div class="card-header"><h3>Action Required</h3></div>
<div class="activity"><div class="activity-icon">!</div><div><strong>Documents required</strong><div>Mokoena Transport</div><div class="activity-time">Due today</div></div></div>
<div class="activity"><div class="activity-icon">⏱</div><div><strong>Quote expiring</strong><div>Commercial Motor</div><div class="activity-time">2 days remaining</div></div></div>
<div class="activity"><div class="activity-icon">↗</div><div><strong>Follow-up required</strong><div>ABC Trading</div><div class="activity-time">3 days overdue</div></div></div>
</div>
</div>

<div class="card">
<div class="card-header"><h3>Recent Activity</h3><a onclick="showPage('applications')">View all</a></div>
<div class="activity"><div class="activity-icon">✓</div><div><strong>Application submitted</strong><div>Commercial Motor · Mokoena Transport</div><div class="activity-time">25 minutes ago</div></div></div>
<div class="activity"><div class="activity-icon">R</div><div><strong>Quote received</strong><div>Business Insurance · ABC Trading</div><div class="activity-time">2 hours ago</div></div></div>
<div class="activity"><div class="activity-icon">+</div><div><strong>New client added</strong><div>Thabo Mokoena</div><div class="activity-time">Yesterday</div></div></div>
</div>
</section>

<section class="page" id="clients">
<div class="page-header"><div><h1>Clients</h1><p>Manage your broker client portfolio.</p></div><button class="primary">+ Add Client</button></div>
<div class="table-card">
<div class="toolbar"><h3>Client Portfolio</h3><input type="search" placeholder="Search clients..."></div>
<div class="table-wrapper"><table>
<thead><tr><th>Client</th><th>Type</th><th>Contact</th><th>Products</th><th>Status</th><th>Last Activity</th><th></th></tr></thead>
<tbody>
<tr><td><strong>Mokoena Transport</strong></td><td>Business</td><td>client@example.com</td><td>Commercial</td><td><span class="status green">Active</span></td><td>Today</td><td><button class="action">View</button></td></tr>
<tr><td><strong>ABC Trading</strong></td><td>Business</td><td>contact@example.com</td><td>Property</td><td><span class="status green">Active</span></td><td>Yesterday</td><td><button class="action">View</button></td></tr>
<tr><td><strong>Thabo Mokoena</strong></td><td>Individual</td><td>thabo@example.com</td><td>Motor</td><td><span class="status blue">New</span></td><td>Yesterday</td><td><button class="action">View</button></td></tr>
<tr><td><strong>Lerato Holdings</strong></td><td>Business</td><td>info@example.com</td><td>Liability</td><td><span class="status yellow">Review</span></td><td>3 days ago</td><td><button class="action">View</button></td></tr>
</tbody>
</table></div></div>
</section>

<section class="page" id="applications">
<div class="page-header"><div><h1>Quotes & Applications</h1><p>Track insurance applications from submission to completion.</p></div><button class="primary">+ New Application</button></div>
<div class="table-card"><div class="toolbar"><h3>Application Pipeline</h3><input type="search" placeholder="Search applications..."></div>
<div class="table-wrapper"><table>
<thead><tr><th>Application</th><th>Client</th><th>Institution</th><th>Product</th><th>Date</th><th>Status</th><th></th></tr></thead>
<tbody>
<tr><td><strong>BB-10025</strong></td><td>Mokoena Transport</td><td>Santam</td><td>Commercial Motor</td><td>17 Sep 2026</td><td><span class="status blue">Submitted</span></td><td><button class="action">View</button></td></tr>
<tr><td><strong>BB-10024</strong></td><td>ABC Trading</td><td>Hollard</td><td>Business Insurance</td><td>16 Sep 2026</td><td><span class="status yellow">Quote Received</span></td><td><button class="action">View</button></td></tr>
<tr><td><strong>BB-10023</strong></td><td>Lerato Holdings</td><td>Old Mutual</td><td>Property</td><td>14 Sep 2026</td><td><span class="status red">Information Required</span></td><td><button class="action">View</button></td></tr>
</tbody></table></div></div>
</section>

<section class="page" id="institutions">
<div class="page-header"><div><h1>Insurance Institutions</h1><p>Browse insurance institutions and available resources.</p></div></div>
<div class="institutions">
<div class="institution"><div class="institution-logo">OM</div><h3>Old Mutual</h3><p>Insurance and financial services provider.</p><div class="tags"><span class="tag">Personal</span><span class="tag">Business</span><span class="tag">Life</span></div><button class="action">View Institution</button></div>
<div class="institution"><div class="institution-logo">S</div><h3>Santam</h3><p>Short-term insurance products.</p><div class="tags"><span class="tag">Motor</span><span class="tag">Commercial</span><span class="tag">Property</span></div><button class="action">View Institution</button></div>
<div class="institution"><div class="institution-logo">H</div><h3>Hollard</h3><p>Insurance products for individuals and businesses.</p><div class="tags"><span class="tag">Motor</span><span class="tag">Business</span><span class="tag">Specialist</span></div><button class="action">View Institution</button></div>
<div class="institution"><div class="institution-logo">D</div><h3>Discovery Insure</h3><p>Insurance products and solutions.</p><div class="tags"><span class="tag">Motor</span><span class="tag">Personal</span></div><button class="action">View Institution</button></div>
<div class="institution"><div class="institution-logo">M</div><h3>Momentum Insure</h3><p>Insurance solutions for personal and business clients.</p><div class="tags"><span class="tag">Motor</span><span class="tag">Business</span></div><button class="action">View Institution</button></div>
<div class="institution"><div class="institution-logo">G</div><h3>Guardrisk</h3><p>Specialist insurance and risk solutions.</p><div class="tags"><span class="tag">Specialist</span><span class="tag">Commercial</span></div><button class="action">View Institution</button></div>
</div>
</section>

<section class="page" id="products">
<div class="page-header"><div><h1>Insurance Products</h1><p>Explore insurance products available to brokers.</p></div></div>
<div class="products">
<div class="product"><h3>Commercial Motor</h3><p>Santam</p><ul><li>Fleet coverage</li><li>Comprehensive cover</li><li>Third-party liability</li><li>Vehicle recovery</li></ul><br><button class="primary">View Product</button></div>
<div class="product"><h3>Business Insurance</h3><p>Hollard</p><ul><li>Business property</li><li>Liability protection</li><li>Business interruption</li><li>Optional extensions</li></ul><br><button class="primary">View Product</button></div>
<div class="product"><h3>Property Insurance</h3><p>Old Mutual</p><ul><li>Building cover</li><li>Contents</li><li>Fire damage</li><li>Additional cover</li></ul><br><button class="primary">View Product</button></div>
<div class="product"><h3>Personal Motor</h3><p>Discovery Insure</p><ul><li>Comprehensive cover</li><li>Accident damage</li><li>Theft protection</li><li>Roadside assistance</li></ul><br><button class="primary">View Product</button></div>
<div class="product"><h3>Specialist Insurance</h3><p>Guardrisk</p><ul><li>Specialist risks</li><li>Tailored solutions</li><li>Commercial risks</li><li>Custom structures</li></ul><br><button class="primary">View Product</button></div>
<div class="product"><h3>Life Insurance</h3><p>Momentum</p><ul><li>Life cover</li><li>Income protection</li><li>Financial planning</li><li>Additional benefits</li></ul><br><button class="primary">View Product</button></div>
</div>
</section>

<section class="page" id="documents">
<div class="page-header"><div><h1>Documents</h1><p>Centralised document management.</p></div><button class="primary">+ Upload Document</button></div>
<div class="table-card"><div class="toolbar"><h3>Document Repository</h3><input type="search" placeholder="Search documents..."></div>
<div class="table-wrapper"><table><thead><tr><th>Document</th><th>Client</th><th>Type</th><th>Date</th><th>Status</th></tr></thead>
<tbody>
<tr><td><strong>Company Registration</strong></td><td>Mokoena Transport</td><td>Supporting</td><td>17 Sep 2026</td><td><span class="status green">Verified</span></td></tr>
<tr><td><strong>Motor Schedule</strong></td><td>ABC Trading</td><td>Policy</td><td>16 Sep 2026</td><td><span class="status green">Verified</span></td></tr>
<tr><td><strong>ID Document</strong></td><td>Thabo Mokoena</td><td>Identity</td><td>15 Sep 2026</td><td><span class="status yellow">Review</span></td></tr>
</tbody></table></div></div>
</section>

<section class="page" id="tasks">
<div class="page-header"><div><h1>Tasks</h1><p>Keep track of outstanding broker activities.</p></div><button class="primary">+ Add Task</button></div>
<div class="task"><div class="task-check"></div><div class="task-info"><strong>Request outstanding documents</strong><small>Mokoena Transport · Due today</small></div><span class="status red">High</span></div>
<div class="task"><div class="task-check"></div><div class="task-info"><strong>Follow up on commercial quote</strong><small>ABC Trading · Due tomorrow</small></div><span class="status yellow">Medium</span></div>
<div class="task"><div class="task-check"></div><div class="task-info"><strong>Review renewal requirements</strong><small>Lerato Holdings · Due Friday</small></div><span class="status blue">Normal</span></div>
</section>

<section class="page" id="reports">
<div class="page-header"><div><h1>Reports</h1><p>Monitor brokerage performance and activity.</p></div></div>
<div class="kpis"><div class="kpi"><div class="kpi-label">Applications</div><div class="kpi-value">124</div></div><div class="kpi"><div class="kpi-label">Completed</div><div class="kpi-value">76</div></div><div class="kpi"><div class="kpi-label">Open</div><div class="kpi-value">24</div></div></div>
<div class="card"><div class="card-header"><h3>Monthly Applications</h3></div><div class="chart">
<div class="bar-group"><div class="bar" style="height:40%"></div><div class="bar-label">Apr</div></div>
<div class="bar-group"><div class="bar" style="height:55%"></div><div class="bar-label">May</div></div>
<div class="bar-group"><div class="bar" style="height:60%"></div><div class="bar-label">Jun</div></div>
<div class="bar-group"><div class="bar" style="height:72%"></div><div class="bar-label">Jul</div></div>
<div class="bar-group"><div class="bar" style="height:68%"></div><div class="bar-label">Aug</div></div>
<div class="bar-group"><div class="bar" style="height:90%"></div><div class="bar-label">Sep</div></div>
</div></div>
</section>

<section class="page" id="resources">
<div class="page-header"><div><h1>Resources</h1><p>Useful information and broker resources.</p></div></div>
<div class="resources">
<div class="resource"><div class="institution-logo">📚</div><h3>Broker Guides</h3><p>Access useful guides and documentation.</p><button class="action">Explore</button></div>
<div class="resource"><div class="institution-logo">🔗</div><h3>Institution Portals</h3><p>Access external insurer resources.</p><button class="action">Explore</button></div>
<div class="resource"><div class="institution-logo">🎓</div><h3>Training</h3><p>Improve your product and broker knowledge.</p><button class="action">Explore</button></div>
</div>
</section>

<section class="page" id="settings">
<div class="page-header"><div><h1>Settings</h1><p>Manage your BrokerBridge preferences.</p></div></div>
<div class="card settings-card">
<h3>Broker Profile</h3>
<div class="form-group"><label>Broker Name</label><input value="Broker Account"></div>
<div class="form-group"><label>Email</label><input value="broker@example.com"></div>
<div class="form-group"><label>Brokerage</label><input value="Insurance Brokerage"></div>
<button class="primary">Save Changes</button>
</div>
</section>

<section class="page" id="support">
<div class="page-header"><div><h1>Help & Support</h1><p>Get assistance with BrokerBridge.</p></div></div>
<div class="resources">
<div class="resource"><div class="institution-logo">?</div><h3>Frequently Asked Questions</h3><p>Find answers to common questions.</p><button class="action">View FAQ</button></div>
<div class="resource"><div class="institution-logo">✉</div><h3>Contact Support</h3><p>Send a message to the support team.</p><button class="action">Contact Support</button></div>
<div class="resource"><div class="institution-logo">!</div><h3>Report a Problem</h3><p>Report an issue with the platform.</p><button class="action">Report Issue</button></div>
</div>
</section>

</div>
</main>
</section>

<script>
const loginForm=document.getElementById("loginForm");

loginForm.addEventListener("submit",e=>{
    e.preventDefault();
    document.getElementById("loginScreen").style.display="none";
    document.getElementById("app").style.display="block";
    localStorage.setItem("brokerBridgeLoggedIn","true");
});

function logout(){
    localStorage.removeItem("brokerBridgeLoggedIn");
    document.getElementById("app").style.display="none";
    document.getElementById("loginScreen").style.display="flex";
}

const navItems=document.querySelectorAll(".nav-item");

navItems.forEach(item=>{
    item.addEventListener("click",()=>{
        showPage(item.dataset.page);
        document.getElementById("sidebar").classList.remove("open");
    });
});

function showPage(pageName){
    document.querySelectorAll(".page").forEach(page=>page.classList.remove("active"));
    const page=document.getElementById(pageName);
    if(page) page.classList.add("active");

    navItems.forEach(item=>{
        item.classList.toggle("active",item.dataset.page===pageName);
    });

    window.scrollTo({top:0,behavior:"smooth"});
}

document.getElementById("mobileMenu").addEventListener("click",()=>{
    document.getElementById("sidebar").classList.toggle("open");
});

if(localStorage.getItem("brokerBridgeLoggedIn")==="true"){
    document.getElementById("loginScreen").style.display="none";
    document.getElementById("app").style.display="block";
}
</script>

</body>
</html>
