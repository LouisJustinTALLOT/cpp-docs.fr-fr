---
title: Intrinsèques du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c05a2843e5daff980d1c84d4d3f2185ac361144d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339014"
---
# <a name="compiler-intrinsics"></a>compilateur, intrinsèques
La plupart des fonctions sont contenues dans des bibliothèques, mais certaines sont intégrées au compilateur (c'est-à-dire intrinsèques). On les appelle des fonctions intrinsèques ou tout simplement des intrinsèques.  
  
## <a name="remarks"></a>Notes  
 Si une fonction est intrinsèque, le code de cette fonction est généralement inséré inline, ce qui évite la surcharge liée à un appel de fonction et permet d'exécuter des instructions machine hautement efficaces pour cette fonction. Une intrinsèque est souvent plus rapide que l'assembly inline équivalent, car l'optimiseur a une connaissance intégrée du comportement de nombreuses intrinsèques. Certaines optimisations peuvent ainsi être disponibles, alors qu'elles ne le sont pas quand un assembly inline est utilisé. De plus, l'optimiseur peut développer l'intrinsèque différemment, aligner les mémoires tampons différemment ou apporter d'autres ajustements en fonction du contexte et des arguments de l'appel.  
  
 L'utilisation d'intrinsèques affecte la portabilité du code, car les intrinsèques disponibles dans Visual C++ peuvent ne pas être disponibles si le code est compilé avec d'autres compilateurs et certaines intrinsèques qui peuvent être disponibles pour certaines architectures cibles ne sont pas disponibles pour toutes les architectures. Toutefois, les intrinsèques sont généralement plus portables que les assemblys inline. Les intrinsèques sont nécessaires sur les architectures 64 bits où les assemblys inline ne sont pas pris en charge.  
  
 Certaines intrinsèques, telles que `__assume` et `__ReadWriteBarrier`, fournissent des informations au compilateur, ce qui affecte le comportement de l'optimiseur.  
  
 Certaines intrinsèques ne sont disponibles que sous la forme d'intrinsèques, tandis que d'autres sont disponibles à la fois dans des implémentations de fonctions et des implémentations intrinsèques. Vous pouvez demander au compilateur d'utiliser l'implémentation intrinsèque de deux façons, selon que vous souhaitez activer uniquement des fonctions spécifiques ou activer toutes les intrinsèques. La première consiste à utiliser `#pragma intrinsic(` *intrinsèque-fonction-nom-list*`)`. Le pragma peut servir à spécifier une ou plusieurs intrinsèques séparées par des virgules. La seconde consiste à utiliser le [/Oi (générer des fonctions intrinsèques)](../build/reference/oi-generate-intrinsic-functions.md) option du compilateur, ce qui rend disponibles les toutes les intrinsèques sur une plateforme donnée. Sous **/Oi**, utilisez `#pragma function(` *intrinsèque-fonction-nom-list* `)` pour forcer un appel de fonction à utiliser au lieu d’une intrinsèque. Si la documentation d’une intrinsèque spécifique indique que la routine est disponible uniquement comme intrinsèque, l’implémentation intrinsèque est utilisée indépendamment du fait que **/Oi** ou `#pragma intrinsic` est spécifié. Dans tous les cas, **/Oi** ou `#pragma intrinsic` permet, mais ne force l’optimiseur à utiliser la fonction intrinsèque. L'optimiseur peut toujours appeler la fonction.  
  
 Certaines fonctions de bibliothèque C/C++ standard sont disponibles dans des implémentations intrinsèques sur certaines architectures. Lorsque vous appelez une fonction CRT, l’implémentation intrinsèque est utilisée si **/Oi** est spécifié sur la ligne de commande.  
  
 Le fichier d’en-tête \<intrin.h >, est disponible qui déclare des prototypes pour les fonctions intrinsèques communes. Intrinsèques spécifiques au fabricant sont disponibles dans le \<immintrin.h > et \<ammintrin.h > fichiers d’en-tête. En outre, certains en-têtes Windows déclarent des fonctions qui mappent à une intrinsèque du compilateur.  
  
 Les sections suivantes répertorient toutes les intrinsèques qui sont disponibles sur différentes architectures. Pour plus d'informations sur le fonctionnement des intrinsèques sur votre processeur cible spécifique, consultez la documentation de référence du fabricant.  
  
-   [ARM, fonctions intrinsèques](../intrinsics/arm-intrinsics.md)  
  
-   [x86, liste de fonctions intrinsèques](../intrinsics/x86-intrinsics-list.md)  
  
-   [x64 (amd64), liste de fonctions intrinsèques](../intrinsics/x64-amd64-intrinsics-list.md)  
  
-   [Fonctions intrinsèques disponibles sur toutes les architectures](../intrinsics/intrinsics-available-on-all-architectures.md)  
  
-   [Liste alphabétique de fonctions intrinsèques](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’assembleur ARM](../assembler/arm/arm-assembler-reference.md)   
 [Référence de Microsoft Macro Assembler](../assembler/masm/microsoft-macro-assembler-reference.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Référence sur les bibliothèques Runtime C](../c-runtime-library/c-run-time-library-reference.md)