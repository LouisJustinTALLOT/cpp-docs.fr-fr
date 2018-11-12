---
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 21d0baccaf74fc08bb110b0ae9f8b7dc108abd6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561574"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

Le compilateur appelle automatiquement la liaison, sauf si vous spécifiez l’option /c. CL fournit un certain contrôle sur l’éditeur de liens par le biais des options de ligne de commande et les arguments. Le tableau suivant récapitule les fonctionnalités du compilateur affectant la liaison.

|Spécification du compilateur|Action du compilateur qui affecte le lien|
|----------------------|---------------------------------|
|Toute extension de nom de fichier autre que .c, .cxx, .cpp ou .def|Transmet un nom de fichier comme entrée de lien|
|*nom de fichier*.def|Passe /DEF :*filename*.def|
|/F*nombre*|Passe/Stack :*nombre*|
|/FD*nom de fichier*|Passe/PDB :*nom de fichier*|
|/Fe*nom de fichier*|Passe/OUT :*nom de fichier*|
|/FM*nom de fichier*|Passe/Map :*nom de fichier*|
|/Gy|Crée des fonctions packagées (COMDAT) ; Active la liaison au niveau des fonctions|
|/LD|Passe /DLL|
|/LDd|Passe /DLL|
|/link|Passe le reste de la ligne de commande à LINK|
|/MD ou /MT|Place un nom de bibliothèque par défaut dans le fichier .obj|
|/ MDd ou /MTd|Place un nom de bibliothèque par défaut dans le fichier .obj. Définit le symbole **_DEBUG**|
|/nologo|Passe /NOLOGO|
|/ Zd|Passes/Debug|
|/ Zi ou/Z7|Passes/Debug|
|/Zl|Omet le nom de la bibliothèque par défaut à partir du fichier .obj|

Pour plus d’informations, consultez l’article [Options du compilateur](../../build/reference/compiler-options.md).

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)