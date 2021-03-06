---
title: /sdl (activer des contrôles de sécurité supplémentaires)
description: L’option/SDL du compilateur Microsoft C/C++ active les vérifications et les avertissements du cycle de vie de développement de sécurité (SDL) recommandés.
ms.date: 10/02/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 8d679bb3fc48e52bcc42a85d507618c38fd3dcdc
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765195"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (activer des contrôles de sécurité supplémentaires)

Active les contrôles de cycle de vie de développement de sécurité (SDL) recommandés. Ces vérifications modifient les avertissements relatifs à la sécurité en erreurs et définissent des fonctionnalités de génération de code sécurisé supplémentaires.

## <a name="syntax"></a>Syntaxe

> **`/sdl`**[**`-`**]

## <a name="remarks"></a>Notes

**/SDL** active un sur-ensemble des vérifications de sécurité de base fournies par [`/GS`](gs-buffer-security-check.md) et les remplacements **`/GS-`** . Par défaut, **`/sdl`** est désactivé. **`/sdl-`** désactive les vérifications de sécurité supplémentaires.

### <a name="compile-time-checks"></a>Vérifications au moment de la compilation

**`/sdl`** active ces avertissements comme des erreurs :

| Avertissement activé par /sdl | Commutateur de ligne de commande équivalent | Description |
|--|--|--|
| [C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md) | /we4146 | Un opérateur moins unaire a été appliqué à un type non signé, ce qui génère un résultat non signé. |
| [C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md) | /we4308 | Une constante intégrale négative a été convertie en type non signé, générant éventuellement un résultat sans signification. |
| [C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md) | /we4532 | L’utilisation `continue` de `break` `goto` Mots clés, ou dans un `__finally` / `finally` bloc a un comportement indéfini au cours d’un arrêt anormal. |
| [C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md) | /we4533 | Le code d'initialisation d'une variable ne sera pas exécuté. |
| [C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) | /we4700 | Utilisation d'une variable locale non initialisée. |
| [C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) | /we4703 | Utilisation d'une variable de pointeur locale potentiellement non initialisée. |
| [C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md) | /we4789 | Dépassement de mémoire tampon quand des fonctions CRT (Runtime C) spécifiques sont utilisées. |
| [C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md) | /we4995 | Utilisation d’une fonction marquée avec pragma [`deprecated`](../../preprocessor/deprecated-c-cpp.md) . |
| [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) | /we4996 | Utilisation d’une fonction marquée comme [`deprecated`](../../cpp/deprecated-cpp.md) . |

### <a name="runtime-checks"></a>Vérifications à l’exécution

Lorsque **`/sdl`** est activé, le compilateur génère du code qui effectue ces contrôles au moment de l’exécution :

- Active le mode strict de **`/GS`** détection du dépassement de mémoire tampon au moment de l’exécution, équivalent à la compilation avec `#pragma strict_gs_check(push, on)` .

- Nettoie le pointeur limité. Dans les expressions qui n’impliquent pas de déréférencement et dans les types qui n’ont pas de destructeur défini par l’utilisateur, les références de pointeur sont définies sur une adresse non valide après un appel à **`delete`** . Cet assainissement permet d’empêcher la réutilisation de références de pointeur obsolètes.

- Initialise les pointeurs de membre de classe. Initialise automatiquement les membres de classe du type pointeur **`nullptr`** sur sur l’instanciation d’objet (avant l’exécution du constructeur). Cela permet d’empêcher l’utilisation de pointeurs non initialisés que le constructeur n’initialise pas explicitement. L’initialisation du pointeur membre générée par le compilateur est appelée, à condition que :

  - L’objet n’est pas alloué à l’aide d’un personnalisé (défini par l’utilisateur) `operator new`

  - L’objet n’est pas alloué dans le cadre d’un tableau (par exemple `new A[x]` )

  - La classe n’est pas gérée ou importée

  - La classe a un constructeur par défaut défini par l’utilisateur.

  Pour être initialisé par la fonction d’initialisation de classe générée par le compilateur, un membre doit être un pointeur, et non une propriété ou une constante.

Pour plus d’informations, consultez [avertissements,/SDL et amélioration de la détection des variables non initialisées](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés général des **Propriétés de configuration**  >  **C/C++**  >  **General** .

1. Définissez la propriété **SDL Checks** à l’aide du contrôle de liste déroulante des propriétés. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
