---
title: Déploiement du CRT universel
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 7952d2ec6e8f502b0edf776811a492c67f495cce
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857230"
---
# <a name="universal-crt-deployment"></a>Déploiement du CRT universel

De Visual Studio .NET jusqu’à Visual Studio 2013, chaque version majeure du compilateur et des outils C++ a inclus une nouvelle version autonome de la bibliothèque Microsoft Runtime C (CRT). Ces versions autonomes du CRT étaient indépendantes les unes des autres et, à différents degrés, incompatibles entre elles. Par exemple, la bibliothèque CRT utilisée par Visual Studio 2012 était la version 11, appelée msvcr110.dll, et la bibliothèque CRT utilisée par Visual Studio 2013 était la version 12, appelée msvcr120.dll. À compter de Visual Studio 2015, ce n’est plus le cas. Visual Studio 2015 et les versions ultérieures de Visual Studio utilisent toutes un seul CRT universel.

Le CRT universel est un composant du système d’exploitation Microsoft Windows. Il est inclus dans le cadre du système d’exploitation dans Windows 10 et est disponible par le biais de Windows Update pour les anciens systèmes d’exploitation (de Windows Vista à Windows 8.1). Par ailleurs, un déploiement local du CRT universel est pris en charge, avec quelques restrictions.

## <a name="central-deployment"></a>Déploiement central

La méthode par défaut pour installer le CRT universel de façon centralisée est d’utiliser Microsoft Windows Update. Comme le CRT universel fait partie des mises à jour recommandées de tous les systèmes d’exploitation Microsoft Windows pris en charge, par défaut, la plupart des machines l’installent dans le cadre du processus de mise à jour normal. La version initiale du CRT universel était [KB2999226](https://support.microsoft.com/kb/2999226). Une mise à jour ultérieure avec différents correctifs de bogue a été appliquée dans [KB3118401](https://support.microsoft.com/kb/3118401), et des mises à jour supplémentaires avec d’autres correctifs de bogues et de nouvelles fonctionnalités ont eu lieu par la suite. Pour connaître les dernières mises à jour, recherchez Runtime C universel ou CRT universel dans [support.microsoft.com](https://support.microsoft.com).

Les ordinateurs Microsoft Windows n’installent pas tous régulièrement les mises à jour à l’aide de Windows Update et certains peuvent ne pas installer les mises à jour recommandées. Pour prendre en charge l’utilisation des applications générées à l’aide des ensembles d’outils Visual Studio 2015 et C++ ultérieurs sur ces ordinateurs, des redistribuables du CRT universel sont disponibles pour une distribution hors connexion. Ces redistribuables peuvent être téléchargés à partir d’un des liens de la Base de connaissances ci-dessus. Notez que les redistribuables du CRT universel nécessitent que l’ordinateur soit mis à jour pour le Service Pack actuel. Par exemple, le redistribuable pour Windows 7 s’installe uniquement sur Windows 7 SP1 et non sur Windows 7 RTM.

Étant donné que la bibliothèque Universal CRT est une dépendance fondamentale de la C++ bibliothèques, l’élément visuel C++ redistribuable (VCRedist) installe la version initiale de la bibliothèque Universal CRT (version 10.0.10240) sur les ordinateurs qui n’ont pas une version est déjà installée. Cette version est suffisante pour répondre à la C++ dépendances de bibliothèque. Si votre application dépend d’une version plus récente de la bibliothèque Universal CRT, vous devez utiliser Windows Update pour mettre votre ordinateur à jour ou installer cette version explicitement. Il est préférable d’avoir le Runtime C universel déjà installé via Windows Update ou par le biais de MSU avant d’installer le VCRedist pour éviter tout plusieurs redémarrages requis.

Pas tous les systèmes d’exploitation sont éligibles pour le Runtime C universel plus récente via Windows Update. Sur Windows 10, la version déployée de manière centralisée, correspond à la version du système d’exploitation. Pour mettre à jour le Runtime C universel en outre, vous devez mettre à jour le système d’exploitation. Pour Windows Vista par le biais de Windows 8.1 la dernière version disponible Runtime C universel est actuellement basé sur la version incluse dans le Windows 10 mise à jour anniversaire, avec des correctifs supplémentaires (version 10.0.14393).

## <a name="local-deployment"></a>Déploiement local

Le déploiement local du CRT universel est pris en charge, bien que non recommandé pour des raisons de performances et de sécurité.  Les DLL pour le déploiement local sont incluses dans le SDK Windows, dans le sous-répertoire Windows Kits\\10\\Redist\\ucrt\\DLLs, par architecture d’ordinateur. Les DLL nécessaires sont notamment ucrtbase.dll et un jeu de DLL de type redirecteur APISet nommé api-ms-win-\*.dll. Comme le jeu de DLL nécessaires varie selon le système d’exploitation, nous vous recommandons vivement d’inclure toutes les DLL quand vous effectuez un déploiement local.

Deux restrictions s’appliquent au déploiement local :

- Sur Windows 10, le CRT universel dans le répertoire système est toujours utilisé, même si une application inclut une copie locale du CRT universel. Cela est vrai même si la copie locale du CRT universel est plus récente. C’est parce que le CRT universel est un composant principal du système d’exploitation sur Windows 10.

- Dans les versions de Windows antérieures à Windows 8, le CRT universel ne peut pas être empaqueté localement avec un plug-in situé dans un répertoire autre que celui contenant le fichier exécutable principal de votre application. Les DLL de type redirecteur APISet ne peuvent pas résoudre ucrtbase.dll dans ce cas. Voici quelques solutions alternatives recommandées :

  - Liez statiquement le CRT universel,
  - Déployez de manière centralisée le CRT universel ou
  - Placez les fichiers du CRT universel dans le même répertoire que l’application.

## <a name="deployment-on-microsoft-windows-xp"></a>Déploiement sur Microsoft Windows XP

Visual Studio 2015 et Visual Studio 2017 continuent à prendre en charge le développement de logiciels pour Microsoft Windows XP. Une version du CRT universel fonctionne donc sur Microsoft Windows XP. Comme le système d’exploitation Microsoft Windows XP n’est plus inclus dans le support standard ou étendu, le déploiement central du CRT universel sur Microsoft Windows XP est différent des autres systèmes d’exploitation.

Quand le redistribuable Visual C++ est installé sur Windows XP, il installe directement le CRT universel et toutes ses dépendances dans le répertoire système, sans installer une mise à jour Windows ni en dépendre. Les modules de fusion redistribuables, les fichiers Microsoft_VC*version*_CRT_\*.msm, font la même chose.

Le déploiement local du CRT universel sur Windows XP est le même que sur les autres systèmes d’exploitation pris en charge.

## <a name="see-also"></a>Voir aussi

- [Déploiement dans Visual C++](deployment-in-visual-cpp.md)
