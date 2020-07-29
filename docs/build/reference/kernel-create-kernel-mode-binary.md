---
title: /kernel (Créer un fichier binaire pour le mode noyau)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: bcef52144e4da932e9e1b6acbcd5f2170c4c7f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211942"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Créer un fichier binaire pour le mode noyau)

Crée un fichier binaire qui peut être exécuté dans le noyau Windows.

## <a name="syntax"></a>Syntaxe

```
/kernel[-]
```

## <a name="arguments"></a>Arguments

**/kernel**<br/>
Le code du projet actuel est compilé et lié à l’aide d’un jeu de règles du langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.

**/kernel**<br/>
Le code du projet actuel est compilé et lié sans utiliser les règles du langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.

## <a name="remarks"></a>Notes

Il n’existe aucun `#pragma` équivalent pour contrôler cette option.

La spécification de l’option **/kernel** indique au compilateur et à l’éditeur de liens d’arbitrer les fonctionnalités de langage qui sont autorisées en mode noyau et de s’assurer que vous disposez d’une puissance d’expressivité suffisante pour éviter l’instabilité du runtime propre au C++ en mode noyau. Cela est accompli en interdisant l’utilisation des fonctionnalités du langage C++ qui sont perturbatrices en mode noyau et en fournissant des avertissements pour les fonctionnalités du langage C++ qui sont potentiellement perturbatrices, mais qui ne peuvent pas être désactivées.

L’option **/kernel** s’applique aux phases du compilateur et de l’éditeur de liens d’une build et est définie au niveau du projet. Passez le commutateur **/kernel** pour indiquer au compilateur que le fichier binaire résultant, après la liaison, doit être chargé dans le noyau Windows. Le compilateur va réduire le spectre des fonctionnalités du langage C++ à un sous-ensemble compatible avec le noyau.

Le tableau suivant répertorie les modifications apportées au comportement du compilateur lorsque **/kernel** est spécifié.

|Type de comportement|**/kernel** Comportement|
|-------------------|---------------------------|
|Gestion d'exceptions C++|Désactivé. Toutes les instances des **`throw`** **`try`** Mots clés et émettent une erreur du compilateur (à l’exception de la spécification d’exception `throw()` ). Aucune option **/Eh** n’est compatible avec **/kernel**, à l’exception de **/Eh-**.|
|RTTI|Désactivé. Toutes les instances des **`dynamic_cast`** **`typeid`** Mots clés et émettent une erreur du compilateur, sauf si **`dynamic_cast`** est utilisé de manière statique.|
|`new` et `delete`|Vous devez définir explicitement l' `new()` `delete()` opérateur or ; ni le compilateur, ni le runtime ne fourniront une définition par défaut.|

Les conventions d’appel personnalisées, l’option de build [/GS](gs-buffer-security-check.md) et toutes les optimisations sont autorisées lorsque vous utilisez l’option **/kernel** . L’incorporation n’est en grande partie pas affectée par **/kernel**, avec la même sémantique honorée par le compilateur. Si vous souhaitez vous assurer que le **`__forceinline`** qualificateur d’incorporation est respecté, vous devez vous assurer que le [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) d’avertissement est activé pour que vous sachiez quand une **`__forceinline`** fonction particulière n’est pas Inline.

Quand le commutateur **/kernel** est passé au compilateur, il prédéfinit une macro de préprocesseur nommée `_KERNEL_MODE` et a la valeur **1**. Vous pouvez l’utiliser pour compiler de façon conditionnelle le code selon que l’environnement d’exécution est en mode utilisateur ou en mode noyau. Par exemple, le code suivant spécifie que la classe doit être dans un segment de mémoire non paginable lorsqu’elle est compilée pour l’exécution en mode noyau.

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

Certaines combinaisons suivantes de l’architecture cible et de l’option **/ARCH** génèrent une erreur lorsqu’elles sont utilisées avec **/kernel**:

- **/arch : {SSE&#124;SSE2&#124;AVX}** ne sont pas pris en charge sur x86. Seul **/arch : ia32** est pris en charge avec **/kernel** sur x86.

- **/arch : AVX** n’est pas pris en charge avec **/kernel** sur x64.

La génération avec **/kernel** passe également **/kernel** à l’éditeur de liens. La manière dont cela affecte le comportement de l’éditeur de liens :

- La liaison incrémentielle est désactivée. Si vous ajoutez **/INCREMENTAL** à la ligne de commande, l’éditeur de liens émet l’erreur irrécupérable suivante :

   **LIEN : erreur irrécupérable LNK1295 : « /INCREMENTAL » n’est pas compatible avec la spécification « /KERNEL »; lier sans'/INCREMENTAL'**

- L’éditeur de liens inspecte chaque fichier objet (ou tout membre archive inclus dans des bibliothèques statiques) pour voir s’il a pu être compilé à l’aide de l’option **/kernel** , mais pas. Si des instances respectent ce critère, l’éditeur de liens a toujours des liens avec succès, mais peut émettre un avertissement, comme indiqué dans le tableau suivant.

   ||**/kernel** obj|**/kernel-** obj, MASM obj ou cvtresed|Combinaison de **/kernel** et **/kernel-** ne comportaient|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**lien/kernel**|Oui|Oui|Oui avec avertissement LNK4257|
   |**lien**|Oui|Oui|Oui|

   **Objet de liaison LNK4257 non compilé avec/KERNEL ; l’image risque de ne pas s’exécuter**

L’option **/kernel** et l’option **/Driver** fonctionnent indépendamment et n’affectent pas l’autre.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Pour définir l’option du compilateur/kernel dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Dans la zone **options supplémentaires** , ajoutez `/kernel` ou `/kernel-` .

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
