---
description: 'En savoir plus sur : &lt; ccomplex&gt;'
title: '&lt;ccomplex&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ccomplex>
helpviewer_keywords:
- ccomplex header
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: 6c9aa717031238681fa04bc20ab6ca93429553ec
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126674"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Comprend l’en-tête de la bibliothèque C++ standard [\<complex>](complex.md) .

> [!NOTE]
> L’en-tête de la bibliothèque standard C \<complex.h> n’est pas inclus \<ccomplex> dans, car il est effectivement remplacé par les surcharges C++ dans \<complex> et \<cmath> . Cela rend l' \<ccomplex> en-tête redondant. L' \<complex.h> en-tête est déconseillé en C++. L' \<ccomplex> en-tête est déconseillé en c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Spécifications

**En-tête :**\<ccomplex>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Le nom `clog` , qui est déclaré dans \<complex.h> , n’est pas défini dans l' `std` espace de noms en raison de conflits potentiels avec le `clog` déclaré dans [\<iostream>](iostream.md) .

## <a name="see-also"></a>Voir aussi

[\<complex>](complex.md)\
[\<cmath>](cmath.md)\
[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)
