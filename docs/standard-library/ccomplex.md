---
title: '&lt;ccomplex&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ccomplex>
- ccomplex
helpviewer_keywords:
- ccomplex header
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: 5b5383b1eca4fda72f5f9e3a78637373acbcf7ab
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341144"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Comprend l' C++ [ \<> complexe](complex.md)d’en-tête de bibliothèque standard.

> [!NOTE]
> L’en-tête \<> de la bibliothèque standard C Complex. \<h n’est pas inclus dans ccomplex >, car C++ il est effectivement remplacé \<par les surcharges dans les > complexes > et \<cmath. Cela rend l' \<en-tête > ccomplex redondant. L' \<en-tête > Complex. h est déconseillé C++dans. L' \<en-tête > ccomplex est déconseillé dans c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<ccomplex >

**Espace de noms :** std

## <a name="remarks"></a>Notes

Le nom `clog`, qui est déclaré dans \<Complex. h >, n’est pas défini `std` dans l’espace de noms en raison `clog` de conflits potentiels avec le déclaré dans [ \<iostream >](iostream.md).

## <a name="see-also"></a>Voir aussi

[\<> complexe](complex.md)\
[\<cmath>](cmath.md)\
[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[C++vue d’ensemble de la bibliothèque standard](cpp-standard-library-overview.md)\
[Sécurité des threads C++ dans la bibliothèque standard](thread-safety-in-the-cpp-standard-library.md)
