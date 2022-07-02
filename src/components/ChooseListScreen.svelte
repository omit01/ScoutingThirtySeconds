<script>
    import {currentGameScreen, game, localStorage , prevGameScreen} from '../stores/stores.js'
	import InterimScore from './InterimScore.svelte'
    import Settings from './Settings.svelte';
    import { fly } from 'svelte/transition';
	import Toast from './Toast.svelte'
    import wordLists from '../stores/wordsLists.json';

    function startGame() {
        let wordsDatabase = [];
        wordLists.forEach(element => {
            if (element.select) {
                wordsDatabase = wordsDatabase.concat(element.words)
            }
        });

        if(wordsDatabase.length > 1) {
            $game.words = wordsDatabase;
            $localStorage.setItem('game', JSON.stringify($game));
            prevGameScreen.set(InterimScore);
            currentGameScreen.set(InterimScore);
        } else {
            window.pushToast("Selecteer minimaal 1 categorie");
        }
    }
    
</script>

<div class="" in:fly>
    <div class="container-fluid pt-2">
        <div class="row mb-3">
            <div class="col-12">
                <div class="float-end" on:click="{() => currentGameScreen.set(Settings)}">
                    <i class="c-white fas fa-cog"></i>
                </div>
            </div>
        </div>
    </div>
    <div class="vertical-center">
        <div class="container-fluid">
            <div class="row justify-content-center pt-3">
                <div class="col-12 col-md-8 col-lg-6 mb-5 text-center">
                    <h1 class="c-white mb-0">Kies Categorie(en)</h1>
                </div>
            </div>

            <div class="row justify-content-center pt-3 mb-3">
                <div class="col-12 col-md-8 col-lg-6 mb-3">
                    <div class="card bg-orange" on:click="{() => startGame()}">
                        <div class="card-body text-center">
                            <h2 class="c-white">Start Spel</h2>
                        </div>
                    </div>
                </div>
            </div>
            
            {#each wordLists as wordlist}

            <div class="row justify-content-center">
                <div class="col-12 col-sm-8 col-lg-5 mb-3">
                    <div class="card">
                        <div class="card-body c-purple text-center">
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" id="check1" bind:checked={wordlist.select}>
                                <label class="form-check-label" for="check1">
                                    <i class="fas fa-book"></i> {wordlist.name} <small class="float-right">({wordlist.words.length})</small>
                                </label>
                            </div>
                            <hr class="mt-0">
                            <p class="my-0">{wordlist.description}</p>
                        </div>
                    </div>
                </div>
            </div>
            {/each}
           
        
        </div>
    </div>
</div>
<Toast />

<style>
   .form-check {
        font-size: 20px;
   }
</style>