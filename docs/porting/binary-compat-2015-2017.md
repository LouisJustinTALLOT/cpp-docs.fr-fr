---
title: Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2019
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 6365ded349ad08a167b76ca9f6ab43e6e7752987
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587895"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Compatibilité binaire C++ entre Visual Studio 2015 et Visual Studio 2019

Dans Visual Studio 2013, la compatibilité binaire entre les fichiers objets (OBJ), les bibliothèques statiques (LIB), les bibliothèques dynamiques (DLL) et les fichiers exécutables (EXE) générés avec différentes versions de l’ensemble d’outils du compilateur et des bibliothèques runtime n’était pas garantie. 

Dans Visual Studio 2015 et ultérieur, le numéro majeur de l’ensemble d’outils C++ est 14 (v140 pour Visual Studio 2015, v141 pour Visual Studio 2017 et v142 pour Visual Studio 2019). Ce qui veut dire que les bibliothèques runtime et les applications compilées avec l’une des versions du compilateur sont binairement compatibles. Cela signifie que si vous avez une bibliothèque tierce qui a été générée avec Visual Studio 2015, il est inutile de la recompiler pour la consommer à partir d’une application générée avec Visual Studio 2017 ou Visual Studio 2019.

La seule exception à cette règle est que les bibliothèques statiques ou les fichiers objets compilés avec le commutateur de compilateur `/GL` ne sont pas binairement compatibles. 

Quand vous combinez des binaires générés avec différentes versions prises en charge de l’ensemble d’outils MSVC, le redistribuable Visual C++ sur lequel votre application s’exécute ne peut être antérieur à aucune des versions de l’ensemble d’outils utilisées pour générer votre application ou les bibliothèques qu’elle consomme. 

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Mise à niveau C++ de Microsoft Visual Redistributable de visual studio 2015 ou 2017 vers visual studio 2019

Étant donné que nous avons conservé la compatibilité binaire et conservé la version majeure (14) de la même C++ façon pour le package redistribuable visual studio 2015, 2017 et 2019, une seule version du C++ package Visual Studio peut être installée à tout moment. Une version plus récente remplace celle qui est installée. Si vous disposez de Visual C++ Studio 2015 ou 2017 et que vous installez ultérieurement 2019, la version de 2019 remplacera une version antérieure. Étant donné que nous nous assurons que la dernière version aura toutes les fonctionnalités et correctifs de bogues les plus récents, y compris les correctifs de sécurité, nous vous recommandons de toujours mettre à niveau vers la dernière version disponible.

De même, nous n’autorisons pas l’installation d’une version C++ antérieure du package redistribuable Visual sur une machine sur laquelle il existe déjà une version plus récente. L’installation du C++ redistribuable visual studio 2015 ou 2017 sur un ordinateur qui a déjà 2019 entraîne un échec d’installation. L’erreur se présente comme suit :

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

Cette erreur est liée à la conception. Nous vous recommandons de conserver la plus récente installée.

## <a name="see-also"></a>Voir aussi

* [Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
* [Derniers téléchargements Visual C++ Redistributable pris en charge](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
