---
description: En savoir plus sur les options de lien Compiler-Controlled
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 86f03f53fe19f6788528dca421fb6030289fca99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178977"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

Le compilateur CL appelle automatiquement LINK, sauf si vous spécifiez l’option/c. CL fournit un contrôle sur l’éditeur de liens via les options de ligne de commande et les arguments. Le tableau suivant récapitule les fonctionnalités de CL qui affectent la liaison.

|Spécification CL|Action CL qui affecte LINK|
|----------------------|---------------------------------|
|Toute extension de nom de fichier autre que. c,. cxx,. cpp ou. def|Passe un nom de fichier comme entrée à lier|
|*filename*. def|Passe/DEF :*filename*. def|
|/F *nombre*|Passe/STACK :*Number*|
|*Nom de fichier* /FD|Passe/PDB :*filename*|
|/Fe *nom de fichier*|Passe/OUT :*filename*|
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
