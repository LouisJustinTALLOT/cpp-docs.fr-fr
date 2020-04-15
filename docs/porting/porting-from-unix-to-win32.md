---
title: Exécution de programmes Linux sur Windows
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: c91bcf1c9384cd71811d42a14b98dc155626a4d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368469"
---
# <a name="running-linux-programs-on-windows"></a>Exécution de programmes Linux sur Windows

Pour exécuter un programme Linux sur Windows, vous avez les options suivantes :

- Exécutez le programme tel quel sur le sous-système Windows pour Linux (WSL). Dans WSL, votre programme s’exécute directement sur le matériel de l’ordinateur, et non sur une machine virtuelle. WSL permet également les appels de système de fichiers directs entre les systèmes Windows et Linux, ce qui élimine le besoin de transport SSL. WSL est conçu comme un environnement de ligne de commande et n’est pas recommandé pour les applications gourmandes en graphisme. Pour plus d’informations, consultez [Documentation du sous-système Windows pour Linux](/windows/wsl/about).
- Exécutez le programme tel quel dans une machine virtuelle Linux ou un conteneur Docker, sur votre ordinateur local ou sur Azure. Pour plus d’informations, consultez [Machines virtuelles](https://azure.microsoft.com/services/virtual-machines/) et [Docker sur Azure](https://docs.microsoft.com/azure/docker/).
- Compilez le programme avec gcc ou clang dans les environnements [MinGW](http://MinGW.org/) ou [MinGW-w64](https://sourceforge.net/p/mingw-w64/wiki2/Home/), qui fournissent une couche de traduction des appels de système Linux vers Windows.
- Compilez et exécutez le programme avec gcc ou clang dans l’environnement [Cygwin](https://www.cygwin.com/), qui fournit un environnement Linux plus complet sur Windows, comparé à MinGW ou MinGW-w64.
- Portez manuellement votre code à partir de Linux et compilez pour Windows avec Microsoft C++ (MSVC). Cela implique la refactorisation du code indépendant de la plateforme dans des bibliothèques distinctes, puis la réécriture de code spécifique à Linux pour utiliser du code spécifique à Windows (par exemple, les API Win32 ou DirectX). Pour les applications qui nécessitent un graphisme hautes performances, il s’agit probablement de la meilleure option.
