<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-light">
            <div class="container ">
                <a class="navbar-brand" href="#"><img src="../assets/logo.jpg"> </a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav  mb-2 mb-lg-0">
                    <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="#">About</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="#">Blog</a>
                    </li>
                    <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="#">Contact</a>
                    </li>
                    
                </ul>
                <!-- <form class="d-flex">
                    <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success" type="submit">Search</button>
                </form> -->
                </div>
            </div>
        </nav>
    </div>
</template>
<script>

export default {
name: 'NavbarSection',
 
    
}
</script>
<style>
    nav{
    font-family: 'Quicksand', sans-serif;
    font-weight:500;
    }
    .navbar-toggler{
        background: #4120a252!important;
        border: 0;
        box-shadow: 2px 7px 10px #4120a22a
    }
</style>