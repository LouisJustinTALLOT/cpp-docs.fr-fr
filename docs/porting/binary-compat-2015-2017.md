---
title: C++compatibilité binaire entre Visual Studio 2015 et Visual Studio 2019
description: Décrit le fonctionnement de la compatibilité binaire C++ entre les fichiers compilés dans Visual Studio 2015, 2017 et 2019. Un package redistribuable Microsoft Visual C++ est valable pour les trois versions.
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912879"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++compatibilité binaire entre Visual Studio 2015 et Visual Studio 2019

Dans Microsoft Visual Studio 2013 et versions antérieures, la compatibilité binaire n’est pas garantie entre les fichiers objet (ne comportaient), les bibliothèques statiques (LIBs), les bibliothèques de liens dynamiques (dll) et les fichiers exécutables (exe) qui ont été créés à l’aide de différentes versions de l’ensemble d’outils du compilateur et les bibliothèques Runtime.

Dans Visual Studio 2015 et ultérieur, le numéro majeur de l’ensemble d’outils C++ est 14 (v140 pour Visual Studio 2015, v141 pour Visual Studio 2017 et v142 pour Visual Studio 2019). Cette numérotation reflète le fait que les bibliothèques Runtime et les applications compilées avec l’une de ces versions du compilateur sont compatibles binaires. Par conséquent, si vous avez une bibliothèque tierce créée avec Visual Studio 2015, vous n’avez pas besoin de la recompiler pour l’utiliser à partir d’une application générée avec Visual Studio 2017 ou Visual Studio 2019.

La seule exception à cette règle est que les fichiers objets et les bibliothèques statiques qui sont compilés avec le commutateur `/GL` du compilateur ne sont *pas* compatibles binaires.

Quand vous combinez des fichiers binaires générés avec différentes versions C++ prises en charge de l’ensemble d' C++ outils Microsoft (MSVC), le package redistribuable Visual sur lequel votre application s’exécute ne peut pas être antérieur à l’une des versions d’ensemble d’outils utilisées pour générer votre application ou les bibliothèques qu’elle consomme.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Mettre à niveau le C++ redistribuable Microsoft visual studio 2015 ou 2017 vers visual studio 2019

Étant donné que nous avons conservé la compatibilité binaire et conservé la version majeure (14) de la même C++ façon sur le redistribuable Microsoft visual studio 2015, 2017 et 2019, une seule version du C++ package Visual redistribuable peut être installée à un moment donné. Une version plus récente remplace une version antérieure déjà installée. Si vous disposez C++ de visual studio 2015 ou 2017 et que vous installez ensuite visual studio 2019, la version de 2019 remplace la version antérieure. Étant donné que nous nous assurons que la dernière version dispose de toutes les fonctionnalités et de tous les correctifs de bogues les plus récents (y compris les correctifs de sécurité), nous vous recommandons de toujours mettre à niveau vers la dernière version disponible.

De même, nous ne vous permettons pas d’installer une version antérieure C++ du package redistribuable Visual sur un ordinateur sur lequel une version plus récente est déjà installée. L’installation du C++ package redistribuable visual studio 2015 ou 2017 sur un ordinateur qui dispose déjà de la version 2019 déclenche un échec d’installation. L’erreur ressemble à ce qui suit :

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Cette erreur est liée à la conception. Nous vous recommandons de conserver la version la plus récente installée.

## <a name="see-also"></a>Voir aussi

* [Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
* [Derniers téléchargements Visual C++ Redistributable pris en charge](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
