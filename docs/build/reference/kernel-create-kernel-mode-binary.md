---
title: /kernel (Créer un fichier binaire pour le mode noyau)
description: L’option/Kernel du compilateur Microsoft C/C++ génère et lie des projets pour l’exécution en mode noyau.
ms.date: 09/28/2020
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: 8a8c02a6f102a52afbc52c154ce215ede3f38f74
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509352"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Créer un fichier binaire pour le mode noyau)

Crée un fichier binaire qui peut être exécuté dans le noyau Windows. Le code du projet actuel est compilé et lié à l’aide d’un ensemble simplifié de fonctionnalités du langage C++ qui sont spécifiques au code qui s’exécute en mode noyau.

## <a name="syntax"></a>Syntaxe

> **`/kernel`**

## <a name="remarks"></a>Notes

La spécification de l' **`/kernel`** option indique au compilateur et à l’éditeur de liens d’arbitrer les fonctionnalités de langage qui sont autorisées en mode noyau et de s’assurer que vous disposez d’une puissance d’expressivité suffisante pour éviter l’instabilité du runtime propre au C++ en mode noyau. Cela est fait en interdisant l’utilisation des fonctionnalités du langage C++ qui sont perturbatrices en mode noyau. Le compilateur génère des avertissements pour les fonctionnalités du langage C++ qui sont potentiellement perturbatrices, mais qui ne peuvent pas être désactivées.

L' **`/kernel`** option s’applique aux phases du compilateur et de l’éditeur de liens d’une build et est définie au niveau du projet. Passez le **`/kernel`** commutateur pour indiquer au compilateur que le fichier binaire résultant, après la liaison, doit être chargé dans le noyau Windows. Le compilateur va réduire le spectre des fonctionnalités du langage C++ à un sous-ensemble compatible avec le noyau.

Le tableau suivant répertorie les modifications apportées au comportement du compilateur quand **`/kernel`** est spécifié.

| Type de comportement | **`/kernel`** comportement |
|--|--|
| Gestion des exceptions C++ | Désactivé. Toutes les instances des **`throw`** **`try`** Mots clés et émettent une erreur du compilateur (à l’exception de la spécification d’exception `throw()` ). Aucune **`/EH`** option n’est compatible avec **`/kernel`** , à l’exception de **`/EH-`** . |
| RTTI | Désactivé. Toutes les instances des **`dynamic_cast`** **`typeid`** Mots clés et émettent une erreur du compilateur, sauf si **`dynamic_cast`** est utilisé de manière statique. |
| `new` et `delete` | Vous devez définir explicitement l' `new()` `delete()` opérateur or. Le compilateur et le runtime ne fournissent pas de définition par défaut. |

Les conventions d’appel personnalisées, l' [`/GS`](gs-buffer-security-check.md) option de génération et toutes les optimisations sont autorisées lorsque vous utilisez l' **`/kernel`** option. L’incorporation n’est en grande partie pas affectée par **`/kernel`** , avec la même sémantique honorée par le compilateur. Si vous souhaitez vous assurer que le **`__forceinline`** qualificateur d’incorporation est respecté, vous devez vous assurer que le [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) d’avertissement est activé pour que vous sachiez quand une fonction particulière **`__forceinline`** n’est pas Inline.

Il n’existe aucun `#pragma` équivalent pour contrôler cette option.

Quand le commutateur reçoit le **`/kernel`** commutateur, il prédéfinit une macro de préprocesseur nommée `_KERNEL_MODE` et a la valeur **1**. Vous pouvez utiliser cette macro pour compiler de façon conditionnelle le code selon que l’environnement d’exécution est en mode utilisateur ou en mode noyau. Par exemple, le code suivant spécifie que la `MyNonPagedClass` classe doit être dans un segment de mémoire non paginable lorsqu’elle est compilée pour l’exécution en mode noyau.

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

Certaines des combinaisons suivantes de l’architecture cible et de l' **`/arch`** option génèrent une erreur lorsqu’elles sont utilisées avec **`/kernel`** :

- **`/arch:SSE`**, **`/arch:SSE2`** , **`/arch:AVX`** , **`/arch:AVX2`** et **`/arch:AVX512`** ne sont pas pris en charge sur x86. Seul **`/arch:IA32`** est pris en charge avec **`/kernel`** sur x86.

- **`/arch:AVX`**, **`/arch:AVX2`** et **`/arch:AVX512`** ne sont pas pris en charge avec **`/kernel`** sur x64.

La génération avec **`/kernel`** passe également **`/kernel`** à l’éditeur de liens. Voici comment l’option affecte le comportement de l’éditeur de liens :

- La liaison incrémentielle est désactivée. Si vous ajoutez **`/incremental`** à la ligne de commande, l’éditeur de liens émet l’erreur irrécupérable suivante :

   **erreur irrécupérable LNK1295 : « /INCREMENTAL » n’est pas compatible avec la spécification « /KERNEL »; lier sans'/INCREMENTAL'**

- L’éditeur de liens inspecte chaque fichier objet (ou tout membre archive inclus dans les bibliothèques statiques) pour voir s’il a pu être compilé à l’aide de l' **`/kernel`** option, mais pas. Si des instances respectent ce critère, l’éditeur de liens a toujours des liens avec succès, mais peut émettre un avertissement, comme indiqué dans le tableau suivant.

   | Commande | **`/kernel`** obj | non **`/kernel`** obj, MASM obj ou cvtres obj | Mélange de **`/kernel`** et de non- **`/kernel`** ne comportaient |
   |--|--|--|--|
   | **`link /kernel`** | Oui | Oui | Oui avec avertissement LNK4257 |
   | **`link`** | Oui | Oui | Oui |

   **Objet de liaison LNK4257 non compilé avec/KERNEL ; l’image risque de ne pas s’exécuter**

L' **`/kernel`** option et l' **`/driver`** option fonctionnent indépendamment. Ils n’ont aucun effet sur les uns les autres.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Pour définir l’option du compilateur/kernel dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Dans la zone **options supplémentaires** , ajoutez *`/kernel`* . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
