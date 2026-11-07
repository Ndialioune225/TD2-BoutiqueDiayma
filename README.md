# Boutique Diayma : TD C# et .NET

> ESP, Departement Genie Informatique, **Alioune Ndiaye**
> Code d'origine : <https://github.com/devehod/BoutiqueDiayma2025>

Boutique en ligne **ASP.NET Core MVC** : liste de produits, panier, commande, interface multilingue (anglais, français et maintenant **wolof**).

---

## 1. Recuperer et executer le code

Dans VS Code ouvrir un dossier et dans le terminal taper **git init, git clone et coller `https://github.com/devehod/BoutiqueDiayma2025.git`**
Ce deplacer dans le dossier **P2FixAnAppDotNetCode** et lanncer avec `dotnet run`.

## 2. Projets de la solution

La solution contient un seul projet : **Diayma.csproj**.

## 3. Version du SDK .NET utilisee

Le SDK utilise est le **.NET Core SDK 2.1.202**, le .NET est **.NET Core 2.0**.

## 4. Installation du SDK

Telechargement depuis le site officiel de Microsoft:
<https://builds.dotnet.microsoft.com/dotnet/Sdk/2.1.202/dotnet-sdk-2.1.202-win-x64.exe>

## 5. Mon depot GitHub

<https://github.com/Ndialioune225/TD2-BoutiqueDiayma.git>

## 6. Bugs trouves

### Bug 1 : le total du panier ignore la quantite

Quand on ajoute 2 fois le « Cle USB-64Gb... » a (1000).
La ligne affiche bien un sous-total de 2000, mais le **Total** affiche **1000**.

### Bug 2 : le stock ne diminue jamais apres une commande

Lors d'une commande de 2 « Cle USB-64Gb » (stock 20) puis retour a l'accueil. Le stock affiche toujours **20** au lieu de 18.

## 7. Points d'arret 
Dans le code.

## 8. Ce qui est visite avant l'affichage des produits

### Namespaces
- `P2FixAnAppDotNetCode`
- `P2FixAnAppDotNetCode.Controllers`
- `P2FixAnAppDotNetCode.Components`

### Classes
- `P2FixAnAppDotNetCode.Startup`
- `P2FixAnAppDotNetCode.Controllers.ProductController`
- `P2FixAnAppDotNetCode.Components.CartSummaryViewComponent`

### Méthodes (dans l'ordre d'exécution)
1. `Startup(IConfiguration configuration)` : constructeur, **point e**, `Startup.cs` ligne 20.
2. `ProductController(IProductService productService, ILanguageService languageService)` : constructeur,
   **point b**, `ProductController.cs` ligne 15.
3. `CartSummaryViewComponent(ICart cart)` : constructeur, **point a**, `CartSummaryViewComponent.cs` ligne 12.

### Points d'arrêt non atteints
- **c** : `OrderController(...)` ligne 17 → seulement en cliquant sur « Commander »
- **d** : `CartController(...)` ligne 15 → seulement en ouvrant le panier ou avec « Ajouter au panier »

### Modes de pas à pas utilisés
- **F5 (Continuer)** pour passer d'un point d'arrêt au suivant (e → b → a)
- **Pas à pas principal (F10)** dans chaque constructeur : les lignes sont de simples affectations
- **Pas à pas sortant (Maj+F11)** pour quitter le constructeur et revenir à l'appelant
- **Pas à pas détaillé (F11)** n'est pas nécessaire ici : aucun appel de notre code à l'intérieur de ces constructeurs

## 9. Deploiement en executable Windows

Publication **autonome** pour Windows 64 bits. Le runtime .NET est inclus, donc rien a installer sur le PC cible :

`
cd P2FixAnAppDotNetCode
dotnet publish -c Release -r win-x64 --self-contained true -o bin\Release\publish
`
