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

### Cowboy Hacking 🤠

<img src="http://www.plantuml.com/plantuml/svg/RP9BZXCn54NdNiMb60235afLaa6hQJMV8H8HEtXjlrHC_37-W2B4Ug3NaOrXDor7WieWFdLzNhqxgBkKAUPYZKX7xG95iaZvPBZ-Hot_kL6yfsBothlio3BUHar67BHYi0tv1ClsdcCIBmplCx97rFCXG-d8CcllHDRPC3xTVsdF-sjyBOppBuAbA0_yJ3IFt5oTOSS5Yf7E3srvcmQx71dIb-gc0S-3TaVy487aaUOwylxn1Y6U7r9r7uUgzlsWCrVF-NfGWbk9ZtxMRJU5OBIiuZU6OAVG724DfOG1xJUqYTrg8HiNiadylDJvp2apL44wfNp-RHal_tQ7yfQqurUNSl-_wyDg8HiNicaXMozacuLiM_lkLhXILtLVfx7Jr6dTQTDfAyHkxCDFD7QQEgshEFNmYTQTDfsskCPD-xuWlV7npH1P3RVlc8hq9K0nscbevflNJRkj_U_OgMBD7m00" class="reveal stretch plain" alt-text="">

--

## Design grâce au DSS

<img src="http://www.plantuml.com/plantuml/svg/XLAzRjim4DxlAGxkOXkm0CbEXWn5sWJsrWhnseKMppORYbJ94mgZoFEqtli6Uh4UbQhs8AGQXCFtm_kvku-i0hUrXVXiNAE2gZ7ooPByWwbwvcWq8TKDdx2cUaSX0XiMoUVTLwhOxE_mMqjOYSSRnbePn-JKpX84uPKxY7RoqJidYkwSah3n3ibn49jlgoF52Rwpvd3aGo1o-0CQLJshW_WUUXwRq9sZE7ghYByV3PFeAgjYn0dA9tyLiSn7i684MyBB9SiJHNbEjnXFaRjVDU7qjJ3KFZL4ixToFkOZM362BQ-x7E5N_-5lHh1RS9ufXPysEJnucMhtsr8ROFFqOLi2EOr9SIKhtfAzG9dZGY_UftBlq3VT-NLXyTzmlhYfxivxumn5L2tEvu_RxNm-0t4i5jBw4Dm2bCNVnrOWxIKm7u92sEMGQh3S04WVcDaiWL8hPY5BxalzQuHISP0JMglkfzA4qurVpn3aHdGh9sZxisfiMYqGurvLngRTMNLzWQ0f3lUNNGO0aY1BsOTW9JEv5xgjxHy0" class="reveal stretch" alt-text="Design grâce au DSS">

--

# Comment valider?

--

## Couches dans le Squelette

<img src="http://www.plantuml.com/plantuml/proxy?fmt=svg&src=https://raw.githubusercontent.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/master/docs/figure-f16.24-web.puml?cacheinc=6" class="plain reveal stretch" alt-text="Diagramme de séparation des couches avec une opération système envoyée au contrôleur GRASP">

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
 * démarrer le jeu
 */
public demarrerJeu(req: Request, res: Response, next: NextFunction) {
  let nom = req.params.nom;
  try {
    // Invoquer l'opération système (du DSS) dans le contrôleur GRASP
    let joueur = this.jeu.demarrerJeu(nom);

    (req as any).flash('Nouveau jeu pour ' + nom);  // error in ts: Property 'flash' does not exist on type 'Request'.
    res.status(201)
```

`JeuRouteur.ts` (couche présentation) a une méthode correspondant à l'opération système {.fragment .current-only data-code-focus=1-4}

Mais elle n'a pas la même signature (arguments d'un service Web) {.fragment .current-only data-code-focus=4}

Appel de la vraie opération système `démarrerJeu(nom)` {.fragment .current-only data-code-focus=7-8}

Voir tout le code de [`JeuRouteur.ts` sur GitHub](https://github.com/profcfuhrmanets/log210-jeu-de-des-node-express-ts/blob/f60c624be15cf51c15135a6cec226b9539a65e78/src/routes/JeuRouter.ts#L25). {.fragment .current-only data-code-focus=1-11}

--

## Inspectez votre code

Pour chaque **opération système** du DSS, il doit y avoir:

- Une méthode ayant **exactement le même nom**
- Un Contrôleur GRASP qui reçoit la méthode:
  - **soit** un objet *racine*, un équipement, etc. du MDD
  - **soit** un *contrôleur de cas d'utilisation*, p.ex. **Gestionnaire*Y*** (*Y* == nom du cas d'utilisation)
- Le Contrôleur GRASP **n'est pas dans la couche de présentation**

--

# ⚠️ 

## Vous utilisez un autre framework

Certaines technologies 🤠 peuvent êtres incompatibles avec cette méthodologie de séparation.

**Vous devez respecter la contrainte de la séparation des couches.**
