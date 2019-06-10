---
title: Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2019
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449034"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2019

Dans Visual Studio 2013, la compatibilité binaire entre les fichiers objets (OBJ), les bibliothèques statiques (LIB), les bibliothèques dynamiques (DLL) et les fichiers exécutables (EXE) générés avec différentes versions de l’ensemble d’outils du compilateur et des bibliothèques runtime n’était pas garantie. 

Dans Visual Studio 2015 et ultérieur, le numéro majeur de l’ensemble d’outils C++ est 14 (v140 pour Visual Studio 2015, v141 pour Visual Studio 2017 et v142 pour Visual Studio 2019). Ce qui veut dire que les bibliothèques runtime et les applications compilées avec l’une des versions du compilateur sont binairement compatibles. Cela signifie que si vous avez une bibliothèque tierce qui a été générée avec Visual Studio 2015, il est inutile de la recompiler pour la consommer à partir d’une application générée avec Visual Studio 2017 ou Visual Studio 2019.

La seule exception à cette règle est que les bibliothèques statiques ou les fichiers objets compilés avec le commutateur de compilateur `/GL` ne sont pas binairement compatibles. 

Quand vous combinez des binaires générés avec différentes versions prises en charge de l’ensemble d’outils MSVC, le redistribuable Visual C++ sur lequel votre application s’exécute ne peut être antérieur à aucune des versions de l’ensemble d’outils utilisées pour générer votre application ou les bibliothèques qu’elle consomme. 

## <a name="see-also"></a>Voir aussi

[Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
