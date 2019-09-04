---
title: Intrinsèques du compilateur
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 8c101de6d74a4f2d3073bd220a29f2a0328d2959
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216868"
---
# <a name="compiler-intrinsics"></a>Intrinsèques du compilateur

La plupart des fonctions sont contenues dans des bibliothèques, mais certaines sont intégrées au compilateur (c'est-à-dire intrinsèques). On les appelle des fonctions intrinsèques ou tout simplement des intrinsèques.

## <a name="remarks"></a>Notes

Si une fonction est intrinsèque, le code de cette fonction est généralement inséré inline, ce qui évite la surcharge liée à un appel de fonction et permet d'exécuter des instructions machine hautement efficaces pour cette fonction. Une intrinsèque est souvent plus rapide que l'assembly inline équivalent, car l'optimiseur a une connaissance intégrée du comportement de nombreuses intrinsèques. Certaines optimisations peuvent ainsi être disponibles, alors qu'elles ne le sont pas quand un assembly inline est utilisé. De plus, l’optimiseur peut développer l’intrinsèque différemment, aligner les mémoires tampons différemment ou apporter d’autres ajustements en fonction du contexte et des arguments de l’appel.

L'utilisation d'intrinsèques affecte la portabilité du code, car les intrinsèques disponibles dans Visual C++ peuvent ne pas être disponibles si le code est compilé avec d'autres compilateurs et certaines intrinsèques qui peuvent être disponibles pour certaines architectures cibles ne sont pas disponibles pour toutes les architectures. Toutefois, les intrinsèques sont généralement plus portables que les assemblys inline. Les intrinsèques sont nécessaires sur les architectures 64 bits où les assemblys inline ne sont pas pris en charge.

Certaines intrinsèques, telles que `__assume` et `__ReadWriteBarrier`, fournissent des informations au compilateur, ce qui affecte le comportement de l'optimiseur.

Certaines intrinsèques ne sont disponibles que sous la forme d'intrinsèques, tandis que d'autres sont disponibles à la fois dans des implémentations de fonctions et des implémentations intrinsèques. Vous pouvez demander au compilateur d'utiliser l'implémentation intrinsèque de deux façons, selon que vous souhaitez activer uniquement des fonctions spécifiques ou activer toutes les intrinsèques. La première consiste à utiliser `#pragma intrinsic(` *intrinsèque-Function-name-List*`)`. Le pragma peut servir à spécifier une ou plusieurs intrinsèques séparées par des virgules. La seconde consiste à utiliser l’option du compilateur [/Oi (générer des fonctions intrinsèques)](../build/reference/oi-generate-intrinsic-functions.md) , qui rend toutes les intrinsèques d’une plateforme donnée disponibles. Sous **/OI**, utilisez `#pragma function(` *intrinsèque-Function-name-List* `)` pour forcer l’utilisation d’un appel de fonction à la place d’un intrinsèque. Si la documentation d’une fonction intrinsèque spécifique indique que la routine est disponible uniquement comme intrinsèque, l’implémentation intrinsèque est utilisée que **/OI** ou `#pragma intrinsic` est spécifié. Dans tous les cas ,/OI `#pragma intrinsic` ou autorise, mais ne force pas, l’optimiseur à utiliser l’intrinsèque. L'optimiseur peut toujours appeler la fonction.

Certaines fonctions de bibliothèque C/C++ standard sont disponibles dans des implémentations intrinsèques sur certaines architectures. Lors de l’appel d’une fonction CRT, l’implémentation intrinsèque est utilisée si **/OI** est spécifié sur la ligne de commande.

Un fichier d’en \<-tête, Intro. h >, est disponible. il déclare des prototypes pour les fonctions intrinsèques communes. Les intrinsèques spécifiques au fabricant sont disponibles dans \<les fichiers d’en- \<tête immintrin. h > et ammintrin. h >. En outre, certains en-têtes Windows déclarent des fonctions qui mappent à une intrinsèque du compilateur.

Les sections suivantes répertorient toutes les intrinsèques qui sont disponibles sur différentes architectures. Pour plus d'informations sur le fonctionnement des intrinsèques sur votre processeur cible spécifique, consultez la documentation de référence du fabricant.

- [Intrinsèques ARM](../intrinsics/arm-intrinsics.md)

- [liste d’intrinsèques x86](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64), liste de fonctions intrinsèques](../intrinsics/x64-amd64-intrinsics-list.md)

- [Intrinsèques disponibles sur toutes les architectures](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Liste alphabétique des fonctions intrinsèques](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Voir aussi

[Référence de l’assembleur ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Référence de Microsoft Macro Assembler](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Référence de la bibliothèque Runtime C](../c-runtime-library/c-run-time-library-reference.md)