---
title: Déploiement du CRT universel
description: Découvrez comment, quand et où déployer la bibliothèque Universal CRT pour votre application.
ms.date: 10/23/2020
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 50ab23f3b0276b058685e9c9ef6634caf5a96186
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497208"
---
# <a name="universal-crt-deployment"></a>Déploiement du CRT universel

De Visual Studio .NET jusqu’à Visual Studio 2013, chaque version majeure du compilateur et des outils C++ a inclus une nouvelle version autonome de la bibliothèque Microsoft Runtime C (CRT). Ces versions autonomes du CRT étaient indépendantes les unes des autres et, à différents degrés, incompatibles entre elles. Par exemple, la bibliothèque CRT utilisée par Visual Studio 2012 était la version 11, appelée msvcr110.dll, et la bibliothèque CRT utilisée par Visual Studio 2013 était la version 12, appelée msvcr120.dll. À compter de Visual Studio 2015, ce n’est plus le cas. Visual Studio 2015 et les versions ultérieures de Visual Studio utilisent toutes un seul CRT universel.

Universal CRT (UCRT) est un composant du système d’exploitation Microsoft Windows. Elle est incluse dans le cadre du système d’exploitation dans Windows 10 et Windows Server 2016 ou version ultérieure. Le UCRT est disponible à l’aide de Windows Update sur des systèmes d’exploitation plus anciens qui sont toujours en support étendu. Le déploiement local du CRT universel est pris en charge, avec certaines restrictions.

## <a name="central-deployment"></a>Déploiement central

La méthode par défaut pour installer le CRT universel de façon centralisée est d’utiliser Microsoft Windows Update. Comme le CRT universel fait partie des mises à jour recommandées de tous les systèmes d’exploitation Microsoft Windows pris en charge, par défaut, la plupart des machines l’installent dans le cadre du processus de mise à jour normal. La version initiale du CRT universel était [KB2999226](https://support.microsoft.com/kb/2999226). Une mise à jour ultérieure avec plusieurs correctifs de bogues a été effectuée dans [KB3118401](https://support.microsoft.com/kb/3118401)et des mises à jour supplémentaires ont été apportées avec des correctifs de bogues et de nouvelles fonctionnalités supplémentaires. Pour connaître les dernières mises à jour, recherchez Runtime C universel ou CRT universel dans [support.microsoft.com](https://support.microsoft.com).

Les ordinateurs Microsoft Windows n’installent pas tous régulièrement les mises à jour à l’aide de Windows Update et certains peuvent ne pas installer les mises à jour recommandées. Pour prendre en charge l’utilisation d’applications générées à l’aide des ensembles d’outils Visual Studio 2015 et C++ ultérieurs sur ces ordinateurs, des fichiers redistribuables Universal CRT sont disponibles pour la distribution hors connexion. Ces fichiers redistribuables peuvent être téléchargés à partir de l’un des liens de la base de connaissances ci-dessus. Le package redistribuable Universal CRT requiert que l’ordinateur ait été mis à jour avec le Service Pack actuel. Par exemple, le redistribuable pour Windows 7 s’installe uniquement sur Windows 7 SP1 et non sur Windows 7 RTM.

Étant donné que le CRT universel est une dépendance fondamentale des bibliothèques C++, le Visual C++ Redistributable (VCRedist) installe la version initiale du Universal CRT (version 10.0.10240) sur les ordinateurs qui n’en ont pas déjà installé. Cette version est suffisante pour satisfaire les dépendances de la bibliothèque C++. Si votre application dépend d’une version plus récente du CRT universel, vous devez utiliser Windows Update pour mettre à jour votre ordinateur, ou installer cette version de manière explicite. Il est préférable d’installer le runtime C universel via Windows Update ou un MSU avant d’installer les VCRedist, afin d’éviter les redémarrages potentiellement multiples requis.

Tous les systèmes d’exploitation ne sont pas éligibles pour le runtime C universel le plus récent via Windows Update. Sur Windows 10, la version déployée de manière centralisée correspond à la version du système d’exploitation. Pour mettre à jour le runtime C universel, vous devez mettre à jour le système d’exploitation. Pour Windows Vista via Windows 8.1, le dernier Runtime C universel disponible est actuellement basé sur la version incluse dans la mise à jour anniversaire de Windows 10, avec des correctifs supplémentaires (version 10.0.14393).

## <a name="local-deployment"></a>Déploiement local

Le déploiement local du CRT universel est pris en charge, bien que non recommandé pour des raisons de performances et de sécurité. Les DLL pour le déploiement local sont incluses dans le SDK Windows, dans le sous-répertoire Windows Kits\\10\\Redist\\ucrt\\DLLs, par architecture d’ordinateur. Les DLL nécessaires sont notamment ucrtbase.dll et un jeu de DLL de type redirecteur APISet nommé api-ms-win-\*.dll. L’ensemble des dll requises sur chaque système d’exploitation varie. Il est fortement recommandé d’inclure toutes les dll lorsque vous déployez localement.

Deux restrictions s’appliquent au déploiement local :

- Sur Windows 10, le CRT universel dans le répertoire système est toujours utilisé, même si une application inclut une copie locale du CRT universel. Cela est vrai même lorsque la copie locale est plus récente, car le CRT universel est un composant principal du système d’exploitation sur Windows 10.

- Dans les versions de Windows antérieures à Windows 8, le CRT universel ne peut pas être empaqueté localement avec un plug-in, s’il se trouve dans un répertoire autre que le répertoire de l’exécutable principal de l’application. Les DLL de type redirecteur APISet ne peuvent pas résoudre ucrtbase.dll dans ce cas. Voici quelques solutions alternatives recommandées :

  - Liez statiquement le CRT universel,
  - Déployez de manière centralisée le CRT universel ou
  - Placez les fichiers du CRT universel dans le même répertoire que l’application.

## <a name="deployment-on-microsoft-windows-xp"></a>Déploiement sur Microsoft Windows XP

Visual Studio 2015 et Visual Studio 2017 continuent à prendre en charge le développement de logiciels pour Microsoft Windows XP. Pour prendre en charge ce développement, une version de la bibliothèque Universal CRT fonctionne sur Microsoft Windows XP. Comme le système d’exploitation Microsoft Windows XP n’est plus inclus dans le support standard ou étendu, le déploiement central du CRT universel sur Microsoft Windows XP est différent des autres systèmes d’exploitation.

Lorsque le Visual C++ redistribuable est installé sur Windows XP, il installe directement le CRT universel et toutes ses dépendances dans le répertoire système. Elle n’est pas installée ou ne dépend d’aucune Windows Update. Les modules de fusion redistribuables, les fichiers Microsoft_VC*version*_CRT_\*.msm, font la même chose.

Le déploiement local du CRT universel sur Windows XP est le même que sur les autres systèmes d’exploitation pris en charge.

## <a name="see-also"></a>Voir aussi

- [Déploiement dans Visual C++](deployment-in-visual-cpp.md)
