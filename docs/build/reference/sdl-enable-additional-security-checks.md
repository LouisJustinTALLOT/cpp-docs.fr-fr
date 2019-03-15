---
title: /sdl (activer des contrôles de sécurité supplémentaires)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 0618b796d492395c3e0e5413047ac0260082baff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814200"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (activer des contrôles de sécurité supplémentaires)

Ajoute les vérifications SDL (Security Development Lifecycle) recommandées. Ces vérifications incluent des avertissements supplémentaires relatifs à la sécurité en tant qu’erreurs, ainsi que des fonctionnalités de génération de code sécurisé supplémentaires.

## <a name="syntax"></a>Syntaxe

```
/sdl[-]
```

## <a name="remarks"></a>Notes

**/SDL** Active un sur-ensemble des vérifications de sécurité de ligne de base fournies par [/GS](gs-buffer-security-check.md) et remplace **/GS-**. Par défaut, **/sdl** est désactivé. **/SDL-** désactive les vérifications de sécurité supplémentaires.

## <a name="compile-time-checks"></a>Vérifications au moment de la compilation

**/SDL** Active les avertissements comme des erreurs :

|Avertissement activé par /sdl|Commutateur de ligne de commande équivalent|Description|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Un opérateur moins unaire a été appliqué à un type non signé, ce qui génère un résultat non signé.|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Une constante intégrale négative a été convertie en type non signé, générant éventuellement un résultat sans signification.|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Utilisation de `continue`, `break` ou `goto` mots clés dans un `__finally` / `finally` bloc a un comportement indéfini lors d’un arrêt anormal.|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Le code d'initialisation d'une variable ne sera pas exécuté.|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Utilisation d'une variable locale non initialisée.|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Utilisation d'une variable de pointeur locale potentiellement non initialisée.|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Dépassement de mémoire tampon quand des fonctions CRT (Runtime C) spécifiques sont utilisées.|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Utilisation d’une fonction marquée avec pragma [déconseillée](../../preprocessor/deprecated-c-cpp.md).|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Utilisation d’une fonction marquée en tant que [déconseillée](../../cpp/deprecated-cpp.md).|

## <a name="runtime-checks"></a>Vérifications au moment de l'exécution

Lorsque **/sdl** est activé, le compilateur génère du code pour effectuer ces vérifications au moment de l’exécution :

- Active le mode strict de **/GS** détection des dépassements de mémoire tampon d’exécution, équivalente à la compilation avec `#pragma strict_gs_check(push, on)`.

- Effectue un assainissement de pointeur limité. Dans les expressions qui n'impliquent pas de déréférencements et dans les types qui n'ont aucun destructeur défini par l'utilisateur, les références de pointeur sont définies sur une adresse non valide après un appel à `delete`. Cela contribue à empêcher la réutilisation de références périmées de pointeur.

- Effectue l’initialisation de pointeur de membre de classe. Automatiquement initialise classe les membres de type pointeur à **nullptr** lors de l’instanciation d’objet (avant l’exécution du constructeur). Cela permet d’éviter l’utilisation de pointeurs non initialisés le constructeur n’initialise pas explicitement. L’initialisation de pointeur de membre généré par le compilateur est appelée tant que :

  - L’objet n’est pas allouée à l’aide d’un personnalisé (défini par l’utilisateur) `operator new`

  - L’objet n’est pas allouée dans le cadre d’un tableau (par exemple `new A[x]`)

  - La classe n’est pas gérée ou importée

  - La classe a un constructeur par défaut défini par l’utilisateur.

  Pour être initialisé par la fonction d’initialisation de classe généré par le compilateur, un membre doit être un pointeur et pas une propriété ou une constante.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [avertissements, /sdl et amélioration de la détection des variables non initialisée](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sur le **général** page, sélectionnez l’option à partir de la **vérifications SDL** liste déroulante.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
