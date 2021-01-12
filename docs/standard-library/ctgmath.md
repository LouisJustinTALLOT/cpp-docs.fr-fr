---
description: 'En savoir plus sur : &lt; ctgmath&gt;'
title: '&lt;ctgmath&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ctgmath>
helpviewer_keywords:
- ctgmath header
ms.assetid: ff521893-f445-4dc8-a2f6-699185bb7024
ms.openlocfilehash: 1968422bc32695eb15cff69c53fcaadf63ac5c14
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126583"
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
