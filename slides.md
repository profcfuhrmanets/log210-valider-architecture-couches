---
theme : "beige"
transition: "convex"
highlightTheme: "github"
title: "LOG210: Valider l'architecture en couches"
separator: ^---
verticalSeparator: ^--

---

# LOG210: Valider l'architecture en couches

--

<!-- .slide: id="HackingCowboy" -->
### Hacking Cowboy 🤠

<img src="http://www.plantuml.com/plantuml/svg/RPBBRjGm58RtVegVi00M5PfaPXPLgSfbYSI8DpYrJn9JNu8le17YUQ3FaHV3BfKhGRo8l_p-JlmlSXCJXPIj4V5EkuK2MSHqDboUGSj_JXIFb4qQlKkEBEDjq6J4h1M3xPBEi6nlEKJnml2Oa3o2dkO4fGFBfBqJIIV3-7JxfRwFb_YQ6UilWgKWPtucgaTkAavtuWp5YEjzlRnEWrqA3EbpSME7v-Ceoy8FiP2yewaClNyumnBM-rZiXx4YVfzruk8vNpQAS3lnqK-wtaxBOhGiuZU6OATG7I4DnOWETNLruhJRoFgDR10_d-fyvfWOAYEUOrf_MyRBl-sXl2Nj-DLJkV-_zM6taVKRsR2HxJUomqPsB7rFEroeYt9VexxHq6ZVwD3eACIfRyEFr3SQ6ksBEBJmaVQD3esEkCHL_SCWlV7XJHTOTTVlcBBqUO5YrDtGn5UlgtPT-j-mKzcQFm00" class="reveal stretch plain" alt-text="Cowboy hacking, beaucoup de couplage">

--

## Design grâce au DSS

<img src="http://www.plantuml.com/plantuml/svg/XLAxRjim5DtlLrmuYst00YGx6J8KQHFOMol4QnUQlBBPyA6I50gZoFUqtli7-h5UEb6TGKWr41VdeSF7kOj9XDHP0_59krO4OJ6ceo5UWvPdvg0L8Tas7T6ItL68a7HYoPVTDv99DnX9UgU43dIBtpj2oNQl4pP2QaEMN4BhbMwqs1c2m2RXzePmyiaxnzh-b9EJzWvP6mYbx-I1uWIlf6mQAV4dj48-YJrxxiySjg4_HLQVRIpyST29M2UDY14do1-l8c9TZc3L2BQ4vqlA8yL4g3gCnvZwtvPmAb-2bRT2Evgzb_bGZc3L2BR4AwFtXxGFH6w4N_s7lnx1Ri3vH7dyl2dXthiK-Z-6kW2Rnu_R6iWfp8etikezsJFK9IxKuaFUxYtwjZ-zF5RyTpbVtLJrfqOxJH55X_FvmtOxdy-07Oi57tqORW3gwlLdA-3ZPR0SXehPvH0rMAu1-1nOc8917Yii0eyhkEn_ZL2B5Bp3jUX_2KKutVZr384xeZekeZbNgZNvQO5UYvdVpeYtxGD5SUXUSRa0u80Yfm_3Yk_aZkdEchy0" class="reveal stretch plain" alt-text="Design grâce au DSS">

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

<img src="http://www.plantuml.com/plantuml/proxy?fmt=svg&cache=no&src=https://raw.githubusercontent.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/master/docs/figure-f16.24-web.puml" class="plain reveal stretch" alt-text="Diagramme de séparation des couches avec une opération système envoyée au contrôleur GRASP">

--

<!-- .slide: id="CouchesDSS" -->
## Couches dans le Squelette (DSS)

<img src="http://www.plantuml.com/plantuml/proxy?fmt=svg&cache=no&src=https://raw.githubusercontent.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/master/docs/dss-details-demarrerJeu.puml" class="plain reveal stretch" alt-text="Diagramme de séparation des couches dans un DSS avec une opération système envoyée au contrôleur GRASP">

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
Note: tous les arguments sont de type primitif!
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
/**
 * démarrer le jeu (express route handler)
 */
public demarrerJeu(req: Request, res: Response, next: NextFunction) {
  let nom = req.params.nom;
  try {
    // Invoquer l'opération système (du DSS) dans le contrôleur GRASP
    let joueur = this.jeu.demarrerJeu(nom);

    (req as any).flash('Nouveau jeu pour ' + nom);  // error in ts: Property 'flash' does not exist on type 'Request'.
    res.status(201)
```

`JeuRouteur.ts` a une méthode *route handler* qui prépare l'opération système {.fragment .current-only data-code-focus=1-4}

Elle convertit l'argument `req` d'un service web pour l'appel de l'opération système {.fragment .current-only data-code-focus=4-5}

Appel de l'opération système `démarrerJeu(nom)`, l'argument `nom` est de type primitif `string` {.fragment .current-only data-code-focus=7-8}

Voir tout le code de [`JeuRouteur.ts` sur GitHub](https://github.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/blob/f60c624be15cf51c15135a6cec226b9539a65e78/src/routes/JeuRouter.ts#L25). {.fragment .current-only data-code-focus=1-11}

--

### 🧐Inspectez votre code

Pour chaque **opération système** du DSS, il doit y avoir:

- Une méthode ayant **exactement le même nom**
- Un Contrôleur GRASP qui reçoit la méthode:
  - **soit** un objet *racine*, un équipement, etc. du MDD
  - **soit** un *contrôleur de cas d'utilisation*, p.ex. **Gestionnaire*Y*** (*Y* == nom du cas d'utilisation)
- Le Contrôleur GRASP **n'est pas dans la couche de présentation**
- Des arguments de type primitif (pas d'objets du domaine)

--

### Symptômes de mauvaise conception 1

⚠️ Vous instanciez un objet (`new Devoir(...)`) dans un routeur pour le passer dans une opération système.{align=left}
- 🤠[logique applicative (créer des objets du domaine) dans la couche présentation (routeur)](#HackingCowboy)
- ✔️Arguments avec type primitif dans une opération système
- ✔️GRASP Créateur s'applique dans la couche domaine
- ✔️[Bonne séparation des couches](#CouchesDSS)

--

### Symptômes de mauvaise conception 2

⚠️ Vous avez une méthode *route handler* (avec arguments de requête et réponse HTTP) dans une classe `Université`.{align=left}
- 🤠logique de routeur (couche présentation) se trouve dans une classe de domaine (`Université` est dans la couche domaine)
- ✔️un routeur devrait se trouver dans une classe traitant les routes, p. ex., `JeuRouteur.ts`
- ✔️[bonne séparation des couches](#CouchesDSS)

--

## ⚠️

## Vous utilisez un autre framework?

Certaines technologies 🤠 peuvent être [incompatibles](https://stackoverflow.com/questions/802050/what-is-opinionated-software) avec cette méthodologie de séparation. C'est la raison que nous ne permettons d'utiliser d'autres frameworks pour le laboratoire.

**Vous devez respecter la contrainte de la séparation des couches.**

Note:
Demandez à votre enseignant ou chargé de lab pour de l'aide au besoin.
