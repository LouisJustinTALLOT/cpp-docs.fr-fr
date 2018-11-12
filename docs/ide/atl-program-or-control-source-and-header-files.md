---
title: Fichiers d'en-tête et fichiers sources de contrôle ou de programme ATL
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: dc2fc7a81d2d32e6bc89e1c10b8fe090650db2ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630579"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Fichiers d'en-tête et fichiers sources de contrôle ou de programme ATL

Les fichiers suivants sont créés quand vous créez un projet ATL dans Visual Studio, selon les options que vous sélectionnez pour ce projet.

Tous ces fichiers sont dans le répertoire *NomProj* ainsi que dans le dossier Header Files (fichiers .h) ou dans le dossier Source Files (fichiers .cpp) de l’Explorateur de solutions.

|Nom de fichier|Description|
|---------------|-----------------|
|*NomProj*.h|Fichier Include principal qui contient les définitions d’interface C++ et déclarations GUID des éléments définis dans ATLSample.idl. Il est regénéré par MIDL pendant la compilation.|
|*NomProj*.cpp|Fichier source de programme principal. Il contient l’implémentation des exportations de votre DLL pour un serveur in-process et l’implémentation de `WinMain` pour un serveur local. Dans le cas d’un service, ce fichier implémente en plus toutes les fonctions de gestion du service.|
|Resource.h|Fichier d’en-tête pour le fichier de ressources.|
|StdAfx.cpp|Contient les fichiers StdAfx.h et Atlimpl.cpp.|
|StdAfx.h|Contient les fichiers d’en-tête ATL.|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[Projets CLR](../ide/files-created-for-clr-projects.md)