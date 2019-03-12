---
title: Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2017
ms.date: 09/24/2018
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: d0291ef75bda2e4da994e40ad55d94ae1042e57e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740506"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2017

Dans les versions précédentes de Visual Studio, la compatibilité binaire entre les fichiers objets (OBJ), les bibliothèques statiques (LIB), les bibliothèques dynamiques (DLL) et les fichiers exécutables (EXE) générés avec différentes versions de l’ensemble d’outils du compilateur et des bibliothèques runtime n’était pas garantie. Ce n’est plus le cas dans Visual Studio 2017. Dans Visual Studio 2015 et Visual Studio 2017, le numéro majeur de l’ensemble d’outils C++ est 14 (v140 pour Visual Studio 2015 et v141 pour Visual Studio 2017). Ce qui veut dire que les bibliothèques runtime et les applications compilées avec l’une des versions du compilateur sont, pour la plupart, binairement compatibles. Par exemple, cela signifie que si vous avez une DLL dans Visual Studio 2015, il est inutile de la recompiler pour la consommer à partir d’une application générée avec Visual Studio 2017.

Il existe deux exceptions à cette règle. La compatibilité binaire n’est pas garantie dans les cas suivants :

1. Quand les bibliothèques statiques ou les fichiers objets sont compilés avec l’option de compilateur `/GL`.

2. Lors de l’utilisation de bibliothèques générées avec un ensemble d’outils dont la version est supérieure à l’ensemble d’outils utilisé pour compiler et lier l’application. Par exemple, un programme qui est compilé et lié avec la version 19.12 du compilateur peut utiliser des bibliothèques qui sont compilées avec les versions 19.0 à 19.12. De plus, la compatibilité binaire existe uniquement entre Visual Studio 2015 et Visual Studio 2017. La liaison de programmes 19.x avec des bibliothèques produites par Visual Studio 2013 ou version antérieure n’est pas prise en charge.

## <a name="see-also"></a>Voir aussi

[Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
