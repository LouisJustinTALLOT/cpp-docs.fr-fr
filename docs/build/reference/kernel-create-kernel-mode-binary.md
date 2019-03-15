---
title: /kernel (Créer un fichier binaire pour le mode noyau)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: d065364cf6d3ae824098634c070f3651324aa52a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816449"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Créer un fichier binaire pour le mode noyau)

Crée un fichier binaire qui peut être exécuté dans le noyau Windows.

## <a name="syntax"></a>Syntaxe

```
/kernel[-]
```

## <a name="arguments"></a>Arguments

**/kernel**<br/>
Le code dans le projet actuel est compilé et lié à l’aide d’un ensemble de règles de langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.

**/kernel-**<br/>
Le code dans le projet actuel est compilé et lié sans utiliser les règles de langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.

## <a name="remarks"></a>Notes

Il existe aucune `#pragma` équivalent pour contrôler cette option.

En spécifiant le **/kernel** option indique au compilateur et l’éditeur de liens arbitrer les fonctionnalités de langage sont autorisées en mode noyau et s’assurer que vous disposez de puissance suffisante afin d’éviter une instabilité du runtime qui est unique pour en mode noyau C++. Cela est accompli en interdisant l’utilisation de fonctionnalités du langage C++ qui entraînent des perturbations en mode noyau et en fournissant des avertissements pour les fonctionnalités du langage C++ qui sont des interruptions de service, mais ne peut pas être désactivées.

Le **/kernel** option s’applique aux phases le compilateur et l’éditeur de liens d’une build et est définie au niveau du projet. Passer le **/kernel** permettant d’indiquer au compilateur que le fichier binaire qui en résulte, après avoir lié, doit être chargé dans le noyau Windows. Le compilateur restreindra la gamme de fonctionnalités du langage C++ à un sous-ensemble qui est compatible avec le noyau.

Le tableau suivant répertorie les changements de comportement du compilateur lorsque **/kernel** est spécifié.

|Type de comportement|**/Kernel** comportement|
|-------------------|---------------------------|
|Gestion d'exceptions C++|Désactivé. Toutes les instances de la `throw` et `try` mots clés émettent une erreur du compilateur (à l’exception de la spécification d’exception `throw()`). Ne **/EH** options sont compatibles avec **/kernel**, à l’exception de **/EH-**.|
|RTTI|Désactivé. Toutes les instances de la `dynamic_cast` et `typeid` mots clés émettent une erreur du compilateur, sauf si `dynamic_cast` est utilisée de manière statique.|
|`new` et `delete`|Vous devez définir explicitement la `new()` ou `delete()` opérateur ; le compilateur ni le runtime fournit une définition default.|

Custom conventions d’appel, le [/GS](gs-buffer-security-check.md) option de build et toutes les optimisations sont autorisés lorsque vous utilisez le **/kernel** option. La fonctionnalité inline est en grande partie non affectée par **/kernel**, avec la même sémantique honorée par le compilateur. Si vous souhaitez vous assurer que le `__forceinline` qualificateur de l’incorporation (inlining) est prise en compte, vous devez vous assurer que l’avertissement [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) est activée afin que vous sachiez quand un particulier `__forceinline` fonction n’est pas inline.

Lorsque le compilateur est passé le **/kernel** commutateur, il prédéfinit une macro de préprocesseur qui est nommée `_KERNEL_MODE` et a la valeur **1**. Vous pouvez utiliser cela pour effectuer une compilation conditionnelle code selon que l’environnement d’exécution est en mode utilisateur ou en mode noyau. Par exemple, le code suivant spécifie que la classe doit être dans un segment de mémoire non paginable lorsqu’il est compilé pour l’exécution en mode noyau.

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

Certaines combinaisons suivantes d’architecture cible et le **/arch** option génère une erreur lorsqu’ils sont utilisés avec **/kernel**:

- **/ arch : {SSE&#124;SSE2&#124;AVX}** ne sont pas pris en charge sur x86. Uniquement **/arch : IA32** est pris en charge avec **/kernel** sur x86.

- **/ arch : AVX** n’est pas pris en charge avec **/kernel** sur x64.

Génération avec **/kernel** passe également **/kernel** l’éditeur de liens. Voici comment cela affecte le comportement de l’éditeur de liens :

- Édition des liens incrémentielle sont désactivée. Si vous ajoutez **/ incremental** à la ligne de commande, l’éditeur de liens émet cette erreur irrécupérable :

   **LINK : erreur irrécupérable des LNK1295 : '/ INCREMENTAL' non compatible avec ' / noyau « spécification ; lier sans '/ INCRÉMENTIELLES**

- L’éditeur de liens inspecte chaque fichier objet (ou n’importe quel membre de l’archive inclus à partir de bibliothèques statiques) pour voir si elle pourrait ont été compilé à l’aide de la **/kernel** option mais elle ne était pas. Si toutes les instances répondent à ce critère, l’éditeur de liens lie toujours correctement mais peut émettre un avertissement, comme indiqué dans le tableau suivant.

   ||**/kernel** obj|**/Kernel-** obj, obj MASM, ou cvtresed|Un mélange de **/kernel** et **/kernel-** obj|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**link /kernel**|Oui|Oui|Oui avec avertissement LNK4257|
   |**link**|Oui|Oui|Oui|

   **Objet de liaison de LNK4257 ne pas compilé avec /KERNEL ; image ne peut pas s’exécuter**

Le **/kernel** option et la **/driver** option fonctionnent indépendamment et aucune n’affecte l’autre.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /kernel dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez `/kernel` ou `/kernel-`.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
