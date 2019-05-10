---
title: Fichiers d'en-tête et fichiers sources de contrôle ou de programme ATL
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 15d49cf984e45feeaad454de13c4ab37622000a4
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446581"
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

[Types de fichiers créés pour Visual C++ projets](file-types-created-for-visual-cpp-projects.md)<br>
[Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC](mfc-program-or-control-source-and-header-files.md)<br>
[Projets CLR](files-created-for-clr-projects.md)
