---
description: 'En savoir plus sur : &lt; ctgmath&gt;'
title: '&lt;ctgmath&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ctgmath>
- ctgmath
helpviewer_keywords:
- ctgmath header
ms.assetid: ff521893-f445-4dc8-a2f6-699185bb7024
ms.openlocfilehash: f1033a944699f4c124114c49e0e30f8b30804a1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324693"
---
# <a name="ltctgmathgt"></a>&lt;ctgmath&gt;

En effet, comprend les en-têtes de bibliothèque standard C++ \<complex> et \<cmath> , qui fournissent des macros mathématiques de type générique équivalentes à \<tgmath.h> .

> [!NOTE]
> L’en-tête de la bibliothèque standard C \<tgmath.h> n’est pas inclus \<ctgmath> dans, car il est effectivement remplacé par les surcharges C++ dans \<complex> et \<cmath> . Cela rend l' \<ctgmath> en-tête redondant. L' \<tgmath.h> en-tête est déconseillé en C++. L' \<ctgmath> en-tête est déconseillé en c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Spécifications

**En-tête :**\<ctgmath>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les fonctionnalités de l’en-tête de la bibliothèque standard C \<tgmath.h> sont fournies par les surcharges dans \<complex> et \<cmath> .

## <a name="see-also"></a>Voir aussi

[\<complex>](complex.md)\
[\<cmath>](cmath.md)\
[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)
