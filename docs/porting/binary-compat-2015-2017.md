---
title: Compatibilité binaire C++ 2015-2019
description: Décrit le fonctionnement de la compatibilité binaire C++ entre les fichiers compilés dans Visual Studio 2015, 2017 et 2019. Un package redistribuable Microsoft Visual C++ est valable pour les trois versions.
ms.date: 11/18/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: b729cdcc4a494e60ec58314fe23b02c1816e8412
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188790"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++compatibilité binaire entre Visual Studio 2015, 2017 et 2019

Les ensembles C++ d’outils du compilateur Microsoft (MSVC) dans Visual Studio 2013 et versions antérieures ne garantissent pas la compatibilité binaire entre les versions. Vous ne pouvez pas lier des fichiers objets, des bibliothèques statiques, des bibliothèques dynamiques et des exécutables créés par différentes versions. Les Abi, les formats d’objet et les bibliothèques Runtime sont incompatibles.

Nous avons modifié ce comportement dans Visual Studio 2015, 2017 et 2019. Les bibliothèques et les applications Runtime compilées par l’une de ces versions du compilateur sont compatibles binaires. Elle est reflétée dans C++ le numéro principal de l’ensemble d’outils, qui est 14 pour les trois versions. (La version de l’ensemble d’outils est V140 pour Visual Studio 2015, V141 pour 2017 et V142 pour 2019). Imaginons que vous avez des bibliothèques tierces générées par Visual Studio 2015. Vous pouvez toujours les utiliser dans une application générée par Visual Studio 2017 ou 2019. Il n’est pas nécessaire de recompiler avec un ensemble d’outils correspondant. La dernière version du package redistribuable Microsoft Visual C++ (Redistributable) fonctionne pour toutes.

Il existe trois restrictions importantes en matière de compatibilité binaire :

- Vous pouvez mélanger des fichiers binaires générés par différentes versions de l’ensemble d’outils. Toutefois, vous devez utiliser un ensemble d’outils au moins aussi récent que le fichier binaire le plus récent pour lier votre application. Voici un exemple : vous pouvez lier une application compilée à l’aide de l’ensemble d’outils 2017 à une bibliothèque statique compilée à l’aide de 2019, si elles sont liées à l’aide de l’ensemble d’outils 2019.

- Le redistribuable que votre application utilise présente une restriction de compatibilité binaire similaire. Quand vous combinez des fichiers binaires générés par différentes versions prises en charge de l’ensemble d’outils, la version redistribuable doit être au moins aussi récente que le dernier ensemble d’outils utilisé par un composant d’application.

- Les bibliothèques statiques ou les fichiers objets compilés à l’aide du commutateur [de compilateur/GL (optimisation de l’ensemble du programme)](../build/reference/gl-whole-program-optimization.md) *ne sont pas* compatibles binaires entre les versions. Tous les fichiers objets et les bibliothèques compilées à l’aide de `/GL` doivent utiliser exactement le même ensemble d’outils pour la compilation et le lien final.

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>Mettre à niveau le C++ redistribuable Microsoft visual studio 2015 ou 2017 vers visual studio 2019

Nous avons conservé le numéro de C++ version principale du composant redistribuable Microsoft Visual pour visual studio 2015, 2017 et 2019. Cela signifie qu’une seule instance du redistribuable peut être installée à la fois. Une version plus récente remplace toute ancienne version déjà installée. Par exemple, une application peut installer le package redistribuable à partir de Visual Studio 2015. Ensuite, une autre application installe le package redistribuable à partir de Visual Studio 2019. La version 2019 remplace l’ancienne version, mais comme elles sont compatibles binaires, l’application antérieure continue à fonctionner correctement. Nous nous assurons que la dernière version du package redistribuable dispose de toutes les fonctionnalités les plus récentes, des mises à jour de sécurité et des correctifs de bogues. C’est la raison pour laquelle nous vous recommandons de toujours mettre à niveau vers la dernière version disponible.

De même, vous ne pouvez pas installer un package redistribuable plus ancien quand une version plus récente est déjà installée. Le programme d’installation signale une erreur si vous essayez. Une erreur semblable à celle-ci s’affiche si vous installez le package redistribuable 2015 ou 2017 sur un ordinateur qui dispose déjà de la version 2019 :

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

Cette erreur est liée à la conception. Nous vous recommandons de conserver la version la plus récente. Vérifiez que votre programme d’installation peut effectuer une récupération à partir de cette erreur en mode silencieux.

## <a name="see-also"></a>Voir aussi

[Historique C++ des modifications visuelles](../porting/visual-cpp-change-history-2003-2015.md)\
[Derniers téléchargements Visual C++ Redistributable pris en charge](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
