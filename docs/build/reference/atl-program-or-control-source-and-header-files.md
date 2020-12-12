---
description: 'En savoir plus sur : fichiers de source et d’en-tête de contrôle ou de programme ATL'
title: Fichiers d'en-tête et fichiers sources de contrôle ou de programme ATL
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 05407e74931112a1680fb103c20c4a2022185026
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182786"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Fichiers d'en-tête et fichiers sources de contrôle ou de programme ATL

Les fichiers suivants sont créés quand vous créez un projet ATL dans Visual Studio, selon les options que vous sélectionnez pour ce projet.

Tous ces fichiers se trouvent dans le répertoire *NomProj*, ainsi que dans le dossier Header Files (fichiers .h) ou Source Files (fichiers .cpp) de l’Explorateur de solutions.

|Nom de fichier|Description|
|---------------|-----------------|
|*ProjName*. h|Fichier Include principal qui contient les définitions d’interface C++ et déclarations GUID des éléments définis dans ATLSample.idl. Il est regénéré par MIDL pendant la compilation.|
|*ProjName*. cpp|Fichier source de programme principal. Il contient l’implémentation des exportations de votre DLL pour un serveur in-process et l’implémentation de `WinMain` pour un serveur local. Dans le cas d’un service, ce fichier implémente en plus toutes les fonctions de gestion du service.|
|Resource.h|Fichier d’en-tête pour le fichier de ressources.|
|StdAfx.cpp|Contient les fichiers StdAfx.h et Atlimpl.cpp.|
|StdAfx.h|Contient les fichiers d’en-tête ATL.|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual Studio C++](file-types-created-for-visual-cpp-projects.md)<br>
[Fichiers de source et d’en-tête de contrôle ou de programme MFC](mfc-program-or-control-source-and-header-files.md)<br>
[Projets CLR](files-created-for-clr-projects.md)
