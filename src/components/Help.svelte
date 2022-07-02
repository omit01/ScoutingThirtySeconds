<script>
	import {currentGameScreen, game,  settings, saveSettings, endGame, prevGameScreen, goToHome } from '../stores/stores.js'
    import Home from './Home.svelte'
	import { fly } from 'svelte/transition';
  
    let safari = false;
    let chrome = false;
    let samsungInternet = false;

    let makeTeams = false;
    let startGame = false;
    let rules = false;

    </script>
    
    <div class="container-fluid pt-2 vh-100" in:fly>
        <div class="row mb-3">
            <div class="col-12">
                <div class="float-end" on:click="{() => currentGameScreen.set(Home)}">
                    <i class="c-white fas fa-times"></i>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-12 text-center">
                <h1 class="c-white">Help</h1>
            </div>
        </div>
    
        <div class="container">

            <div class="row justify-content-center">
                <div class="col-12 col-md-8 col-lg-6">
                    <div class="card mb-3">
                        <div class="card-body">
                            <div class="row mb-2 justify-content-center">
                                <div class="col-12">
                                    <h3 class="text-center">Installeren & Updaten</h3>
                                    <p class="mb-0">Deze app is te installeren als Progressive Web App, zodat hij zonder 
                                        internetverbinding is te gebruiken en automatische updates krijgt.
                                    </p>
                                </div>
                            </div>
                            <div class="row justify-content-center">
                                <div class="col-12 text-left">
                                    <hr>
                                    {#if !safari}
                                    <h5 on:click="{() => {safari = !safari}}"><i class="fab fa-apple"></i> Safari <i class="fas float-end d-inline fa-chevron-right"></i></h5>
                                    <hr>
                                    {:else}
                                    <h5 on:click="{() => {safari = !safari}}"><i class="fab fa-apple"></i> Safari <i class="fas float-end d-inline fa-chevron-down"></i></h5>
                                    <hr>
                                    <ol type="1">
                                        <li>Klik op het "delen" icoontje</li>
                                        <li>Klik op "Zet op beginscherm"</li>
                                        <li>Klik op "Voeg toe"</li>
                                    </ol>
                                    {/if}
                                </div>
                            </div>
                            <div class="row justify-content-center">
                                <div class="col-12 text-left">
                                    {#if !chrome}
                                    <h5 on:click="{() => {chrome = !chrome}}"><i class="fab fa-android"></i> Chrome <i class="fas float-end d-inline fa-chevron-right"></i></h5>
                                    <hr>
                                    {:else}
                                    <h5 on:click="{() => {chrome = !chrome}}"><i class="fab fa-android"></i> Chrome <i class="fas float-end d-inline fa-chevron-down"></i></h5>
                                    <hr>
                                    <ol type="1">
                                        <li>Klik op het <i class="fas fa-ellipsis-v"></i> icoontje</li>
                                        <li>Klik op "App installeren"</li>
                                        <li>Klik op "Installeren"</li>
                                    </ol>
                                    {/if}
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="row justify-content-center">
                <div class="col-12 col-md-8 col-lg-6">
                    <div class="card mb-3">
                        <div class="card-body">
                            <div class="row mb-2 justify-content-center">
                                <div class="col-12">
                                    <h3 class="text-center">Spelen</h3>
                                    <p class="mb-0">Uitleg hoe je een spel start en de regels van 30 seconds
                                    </p>
                                </div>
                            </div>
                            <div class="row justify-content-center">
                                <div class="col-12 text-left">
                                    <hr>
                                    {#if !makeTeams}
                                    <h5 on:click="{() => {makeTeams = !makeTeams}}">1. Teams maken <i class="fas float-end d-inline fa-chevron-right"></i></h5>
                                    <hr>
                                    {:else}
                                    <h5 on:click="{() => {makeTeams = !makeTeams}}">1. Teams maken <i class="fas float-end d-inline fa-chevron-down"></i></h5>
                                    <hr>
                                    <p class="">
                                        Voeg een team toe door de teamnaam in te vullen en op de <i class="fas fa-plus-square"></i> knop te klikken. <br>
                                        Voeg vervolgens spelers toe door op het team te klikken, de speler naam in te vullen en op de <i class="fas fa-plus-square"></i> knop
                                        te klikken <br> <br>
                                        Let op: Een team bestaat uit minimaal 2 spelers
                                    </p>
                                    {/if}
                                </div>
                            </div>
                            <div class="row justify-content-center">
                                <div class="col-12 text-left">
                                    {#if !startGame}
                                    <h5 on:click="{() => {startGame = !startGame}}">2. Spel starten <i class="fas float-end d-inline fa-chevron-right"></i></h5>
                                    <hr>
                                    {:else}
                                    <h5 on:click="{() => {startGame = !startGame}}">2. Spel starten <i class="fas float-end d-inline fa-chevron-down"></i></h5>
                                    <hr>
                                    <p class="">
                                        Wanneer er minimaal 2 teams van 2 personen zijn, kan het spel gestart worden door op de knop "Start Spel" te klikken. <br>
                                    </p>
                                    {/if}
                                </div>
                            </div>
                            <div class="row justify-content-center">
                                <div class="col-12 text-left">
                                    {#if !rules}
                                    <h5 on:click="{() => {rules = !rules}}">3. Regels <i class="fas float-end d-inline fa-chevron-right"></i></h5>
                                    <hr>
                                    {:else}
                                     <h5 on:click="{() => {rules = !rules}}">2. Regels <i class="fas float-end d-inline fa-chevron-down"></i></h5>
                                    <hr>
                                    <p class="">
                                        De app toont 5 woorden die de speler in een volgorde naar keuze mag omschrijven. Elk woord dat door het team goed geraden wordt is een punt waard. De app houdt deze punten bij.<br>
                                        De speler die omschrijft, moet zich aan de volgende spelregels houden: <br><br>
                                        
                                        <b>Hij MAG WEL:</b><br>
                                        - de naam op welke manier dan ook omschrijven, waarbij zingen, neuriën en gebaren zijn toegestaan.<br>
                                        - de woorden “en”, ”de”, ”het”, “and”, en “the”, die in sommige namen voorkomen, gebruiken.<br><br>
                                        
                                        <b>Hij MAG NIET:</b><br>
                                        - de namen op de kaart noemen. - namen die van de naam op de kaart zijn afgeleid, noemen.<br>
                                        - “klinkt als”- of “rijmt op”-tactieken gebruiken.<br>
                                        - naar een letter of letters van het alfabet verwijzen.<br>
                                        - naar iets wijzen.<br><br>
                                            
                                        De spelers die raden, roepen hun veronderstellingen, terwijl de speler die omschrijft bezig is. Zij MOGEN de letters van het alfabet WEL gebruiken, zeker als de te omschrijven naam een afkorting is.

                                       </p>
                                    {/if}
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>    
    </div>
    
    
    <style>
    
     
    </style>