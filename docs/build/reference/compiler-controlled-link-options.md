---
title: Options LINK contrôlées par le compilateur
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440110"
---
# <a name="compiler-controlled-link-options"></a>Options LINK contrôlées par le compilateur

Le compilateur CL appelle automatiquement LINK, sauf si vous spécifiez l’option/c. CL fournit un contrôle sur l’éditeur de liens via les options de ligne de commande et les arguments. Le tableau suivant récapitule les fonctionnalités de CL qui affectent la liaison.

|Spécification CL|Action CL qui affecte LINK|
|----------------------|---------------------------------|
|Toute extension de nom de fichier autre que. c,. cxx,. cpp ou. def|Passe un nom de fichier comme entrée à lier|
|*filename*. def|Passe/DEF :*filename*. def|
|/F*nombre*|Passe/STACK :*Number*|
|*Nom de fichier* /FD|Passe/PDB :*filename*|
|/Fe*nom de fichier*|Passe/OUT :*filename*|
|*Nom de fichier* /FM|Passe/MAP :*filename*|
|/Gy|Crée des fonctions packagées (COMDAT); active la liaison au niveau des fonctions|
|/LD|Passe/DLL|
|/LDd|Passe/DLL|
|/link|Passe le reste de la ligne de commande à LINK|
|/MD ou/MT|Place un nom de bibliothèque par défaut dans le fichier. obj|
|/MDd ou/MTd|Place un nom de bibliothèque par défaut dans le fichier. obj. Définit le symbole **_DEBUG**|
|/nologo|Passe/NOLOGO|
|/Zd|Passe/DEBUG|
|/Zi ou/Z7|Passe/DEBUG|
|/Zl|Omet le nom de la bibliothèque par défaut du fichier. obj|

Pour plus d’informations, consultez [Options du compilateur MSVC](compiler-options.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
