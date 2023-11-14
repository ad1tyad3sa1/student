---
comments: false
layout: post
title: Week2 Update
description: What I have accomplished after Week2
type: hacks
courses: { csp: {week: 2}}
---

# Week2 Update

## JS Output with JS inquiry  

**A table of the most popular soccer players right now**

<!-- Head contains information to Support the Document -->
<head>
    <!-- load jQuery and DataTables output style and scripts -->
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>

<!-- Body contains the contents of the Document -->
<body>
    <table id="demo" class="table">
        <thead>
            <tr>
                <th>Name</th>
                <th>Age</th>
                <th>Club</th>
                <th>Country</th>
                <th>Salary</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Messi</td>
                <td>36</td>
                <td>Inter Miami</td>
                <td>Argentina</td>
                <td>$54 million dollars</td>
            </tr>
            <tr>
                <td>Ronaldo</td>
                <td>38</td>
                <td>Al Nassr</td>
                <td>Portugal</td>
                <td>$200 million dollars</td>
            </tr>
            <tr>
                <td>Mbappe</td>
                <td>24</td>
                <td>PSG</td>
                <td>France</td>
                <td>$74 million dollars</td>
            </tr>
            <tr>
                <td>Halaand</td>
                <td>23</td>
                <td>Manchester City</td>
                <td>Norway</td>
                <td>$35 million dollars</td>
            </tr>
            <tr>
                <td>Lewandowski</td>
                <td>35</td>
                <td>Barcelona</td>
                <td>Poland</td>
                <td>$23 million dollars</td>
            </tr>
            <tr>
                <td>Modric</td>
                <td>37</td>
                <td>Real Madrid</td>
                <td>Croatia</td>
                <td>$20 million dollars</td>
            </tr>
            <tr>
                <td>Benzema</td>
                <td>35</td>
                <td>Al Ittihad</td>
                <td>France</td>
                <td>$10 million dollars</td>
            </tr>
            <tr>
                <td>Neymar</td>
                <td>31</td>
                <td>Al Hilal</td>
                <td>Brazil</td>
                <td>$41 million dollars</td>
            </tr>
            <tr>
                <td>Salah</td>
                <td>31</td>
                <td>Liverpool</td>
                <td>Egypt</td>
                <td>$19 million dollars</td>
            </tr>
            <tr>
                <td>De Bruyne</td>
                <td>32</td>
                <td>Manchester City</td>
                <td>Belgium</td>
                <td>$21 million dollars</td>
            </tr>
            <tr>
                <td>Kane</td>
                <td>30</td>
                <td>Bayern Munich</td>
                <td>England</td>
                <td>$15 million dollars</td>
            <tr>
                <td>Reus</td>
                <td>34</td>
                <td>Borrusia Dortmund</td>
                <td>Germany</td>
                <td>$11 million dollars</td>
            </tr>
            <tr>
                <td>Son</td>
                <td>31</td>
                <td>Tottenham Hotspurs</td>
                <td>South Korea</td>
                <td>$10 million dollars</td>
            </tr>
            <tr>
                <td>Saka</td>
                <td>21</td>
                <td>Arsenal</td>
                <td>England</td>
                <td>$9 million dollars</td>
            </tr>
            <tr>
                <td>Rashford</td>
                <td>25</td>
                <td>Manchester United</td>
                <td>England</td>
                <td>$11 million dollars</td>
            </tr>
        </tbody>
    </table>
</body>

<!-- Script is used to embed executable code -->
<script>
    $("#demo").DataTable();
</script>
