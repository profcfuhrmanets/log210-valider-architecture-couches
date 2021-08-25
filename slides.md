---
theme : "beige"
transition: "convex"
highlightTheme: "github"
title: "LOG210: Valider l'architecture en couches"
separator: ^---
verticalSeparator: ^--
logoImg: assets/logo_ets.svg
notesSeparator: "Note:"
showProgress: true

---

# LOG210: Valider l'architecture en couches

--

<!-- .slide: id="HackingCowboy" -->
### Hacking Cowboy 🤠

<img src="http://www.plantuml.com/plantuml/svg/RPBBRjGm58RtVegVi00M5PfaPXPLgSfbYSI8DpYrJn9JNu8le17YUQ3FaHV3BfKhGRo8l_p-JlmlSXCJXPIj4V5EkuK2MSHqDboUGSj_JXIFb4qQlKkEBEDjq6J4h1M3xPBEi6nlEKJnml2Oa3o2dkO4fGFBfBqJIIV3-7JxfRwFb_YQ6UilWgKWPtucgaTkAavtuWp5YEjzlRnEWrqA3EbpSME7v-Ceoy8FiP2yewaClNyumnBM-rZiXx4YVfzruk8vNpQAS3lnqK-wtaxBOhGiuZU6OATG7I4DnOWETNLruhJRoFgDR10_d-fyvfWOAYEUOrf_MyRBl-sXl2Nj-DLJkV-_zM6taVKRsR2HxJUomqPsB7rFEroeYt9VexxHq6ZVwD3eACIfRyEFr3SQ6ksBEBJmaVQD3esEkCHL_SCWlV7XJHTOTTVlcBBqUO5YrDtGn5UlgtPT-j-mKzcQFm00" class="reveal stretch plain" alt-text="Cowboy hacking, beaucoup de couplage">

--

## Design grâce au DSS

<img src="http://www.plantuml.com/plantuml/svg/XL9BRjiy4DxFAGREnZPW0PQTBBBuaRy9x5rhnDjkQ79ai-539KSjZ2BdQRtl3NInZfog3WeXrO8OV0zzm-7SPLQ96-yWFzbGgwGyPZuwaZDP_HUpK_ffds8JZ8uk9kIaGXQA0iF16aBoDH_HazzHoi2M7U67tIVIR2lCf6CmoYQwnSyDePQGQ1ahfQqZJu7HHsChgtQE88b9XRqZ7BsB8OYsFNLTi8q1HPi8TMpqWV88hxIkAgtn6zJIeTgBv_xCOPtQKnRrsIR2hmVB93hjLCuuGldaL1atym6i7C0My7n9UQJCXAR1VCpS_l24O_qIRA9NDj3ahSo7-G1M3c0Bl79sV-1z8We3_F8V_FK0TWCXCdNb-_KSxcFWrFvqr2HOF_w_tG05WvtYbQnyI_OCcpdEpEo_hjrRZ7LxUdci_6Su7yFOjAVA1aiPLOFJwSDsEvrEG1opcLozBsu0DkNldor1hjU1yxueXLtqKRtb6a3kWOKh19Ion28LdVlI_mfXepZ5W2lLVbU6SBoEgmc2x8XfBACxhrJjkgS5wXRpIqms4phrUll0KEvthxWC02IWwDBxOYapkHEwyUuN" class="reveal stretch plain" alt-text="Design grâce au DSS">

--

## Avantages de la séparation en couches

- On peut remplacer la couche présentation (Express) avec une autre plus facilement
- Les classes domaine sont plus cohésives
  - plus faciles à comprendre
  - plus réutilisables dans une autre application

--

# Comment valider?

--

## Couches dans le Squelette

<img src="http://www.plantuml.com/plantuml/proxy?fmt=svg&cache=no&src=https://raw.githubusercontent.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/master/docs/modeles/figure-f16.24-web.puml" class="plain reveal stretch" alt-text="Diagramme de séparation des couches avec une opération système envoyée au contrôleur GRASP">

--

<!-- .slide: id="CouchesDSS" -->
## Couches dans le Squelette (DSS)

<img src="http://www.plantuml.com/plantuml/proxy?fmt=svg&cache=no&src=https://raw.githubusercontent.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/master/docs/modeles/dss-details-demarrerJeu.puml" class="plain reveal stretch" alt-text="Diagramme de séparation des couches dans un DSS avec une opération système envoyée au contrôleur GRASP">

--

## DSS du squelette

<style>
.container{display: flex;}
.col{flex: 1;}
</style>

<div class="container">
<div class="col">

![DSS pour un scénario Jouer aux dés](https://www.plantuml.com/plantuml/svg/NP71JiCm38RlUGfhfrNgG5odQHg2qmIdIfnsCQbN0erJ74TYGhmFUuw-62xJ95WEaUB_j_tPsMH5qH9xbzy23oWO8UkX9xib-0kbfJsMNlU9bJ4IF96qoFWtbzuBiIVuT63daNB6Zcxxq35uOYLnNqw3MeFxfe4X5O72aFruP9IGO1NMsrH80Ci7jECnhwx3UiVpkvShk340U429o9L3hqbWjfpSHMQ06Rmp20q-3CXgKdF8Edv7-XMpyujrXkLKDA88oPRAd5EqK6EpSbUvFgK11ZCRPmmy7iyvhnFIXTcl5ej9isWDcXHxQ0lqQDDB3I36Rhj2XNc7dTM2L62mXPMgtZ4_JxESpBc6VyyfjUGSiYDkOM8wOvomJkILsvXi__C3){style=max-width:105%;}{class=plain}

</div>

<div class="col">

Trois opérations système:
1. `démarrerJeu(nom:String)`
2. `jouer(nom:String)`
3. `terminerJeu()`
> Tous les arguments sont de type primitif!
</div>
</div>

--

## Opération système

- Il y a une méthode `démarrerJeu(nom:String)` dans `JeuDeDés` (un contrôleur GRASP).
- `JeuDeDés` est l'objet racine du MDD.

<img src="https://www.plantuml.com/plantuml/svg/NP1DQiCm44RtEiM7Drsva2wzA85c5TfLeVkfDOdLwiT8eu8flKzp3b-iOnEIaer6VE_D3DAs26MfmPlowU98cGAAJ9xrpAw_8POFLBqSKfH8WV76sL8au_aWa8JiZeF0kiozk1JDu2o3moWJ0eTtpiNSNQTv5rccaP6o3Cc84rtxakpygzLMs1H85OofPcYqPysKpAUouAVX7fibUAOSA9hUKodOfyggVniWfe0Eh_gEU3G_PxwRJoly8hzu7LoK2zGDErQZ67EvejaqQ5iq3ytQl7JqlWeUOSxBLiEtQxtsTVXGVAlz7-GfzgkmvMZrf_y0" class="reveal stretch" alt-text="MDD">

--

## Opération système codée

<!-- .slide: data-background="#ddFFdd" -->

```Typescript
/* démarrer le jeu (express route handler) */
public demarrerJeu(req: Request, res: Response, next: NextFunction) {
  const nom = req.body.nom;
  try {
    // Invoquer l'opération système (du DSS) dans le contrôleur GRASP
    const joueur = this._controleurJeu.demarrerJeu(nom);
    const joueurObj = JSON.parse(joueur);
    req.flash('info', `Nouveau jeu pour ${nom}`);
    // ...
  }
}
```

`JeuRouteur.ts` a une méthode *route handler* qui invoque l'opération système {.fragment .current-only data-code-focus=2}

Elle décortique l'argument `req` d'un service web pour extraire les arguments de l'opération système {.fragment .current-only data-code-focus=3}

Appel de l'opération système `démarrerJeu(nom)`, l'argument `nom` est de type primitif `string` {.fragment .current-only data-code-focus=5-6}

L'objet de retour est une copie de l'objet Joueur (du domaine), pour respecter la séparation des couches. {.fragment .current-only data-code-focus=7}

Voir tout le code de [`JeuRouteur.ts` sur GitHub](https://github.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/blob/609846674a0a454bd1e22d364ef10515018ec81e/src/routes/JeuRouter.ts#L29-L52). {.fragment .current-only data-code-focus=1-11}

--

<!-- .slide: data-background="#ffccff" -->
### 🧐Inspectez votre code

Pour chaque **opération système** du DSS, il doit y avoir:

- une méthode ayant **exactement le même nom**,
- des arguments de type primitif,
- un Contrôleur GRASP qui reçoit la méthode:
  - **soit** un objet *racine*, un équipement, etc. du MDD. C'est un *contrôleur de façade*.
  - **soit** un *contrôleur de cas d'utilisation*, ex. **Gestionnaire*Y*** (*Y* == nom du cas d'utilisation)

Notez que le Contrôleur GRASP **n'est pas dans la couche de présentation**

--

### Symptômes de mauvaise conception 1

⚠️ Vous instanciez un objet (`new Devoir(...)`) dans un routeur pour le passer dans une opération système. {align=left}

- 🤠[Logique applicative (créer des objets du domaine) dans la couche présentation (routeur)](#HackingCowboy).

Correctif:

- ✔️Passer les arguments de type primitif dans une opération système ([éventuellement refactoriser](https://refactoring.com/catalog/introduceParameterObject.html)).
- ✔️Appliquer GRASP Créateur pour instancier l'objet du domaine dans la couche domaine.
- ✔️[Bonne séparation des couches](#CouchesDSS).

--

### Symptômes de mauvaise conception 2

⚠️ Vous avez une méthode *route handler* (avec arguments de requête et réponse HTTP) dans une classe `Université`. {align=left}

- 🤠Logique de routeur (couche présentation) se trouve dans une classe de domaine (`Université`).

Correctif:

- ✔️Un routeur devrait se trouver dans une classe traitant les routes, ex. `JeuRouteur.ts`.
- ✔️[Bonne séparation des couches](#CouchesDSS).

--

## ⚠️

## Vous utilisez un autre framework?

Certaines technologies 🤠 peuvent être [incompatibles](https://stackoverflow.com/questions/802050/what-is-opinionated-software) avec cette méthodologie de séparation. C'est la raison que nous ne permettons pas l'utilisation d'autres cadriciels pour le laboratoire.

**Vous devez respecter la contrainte de la séparation des couches.**

Note:
Demandez à votre enseignant ou chargé de lab pour de l'aide au besoin.
