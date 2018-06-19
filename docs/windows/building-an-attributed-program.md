---
title: Création d’un programme avec attributs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d87f95b456e3f99598f48e6ffa8ad29806aa168
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862275"
---
# <a name="building-an-attributed-program"></a>Générer un programmes par attributs
Après avoir mis les attributs Visual C++ dans votre code source, vous souhaiterez le compilateur Visual C++ pour produire un fichier .idl et de la bibliothèque de type pour vous. Des options de l’éditeur de liens suivant vous aident à générer des fichiers .tlb et .idl :  
  
-   [OPTION /IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 Certains projets contiennent plusieurs fichiers .idl indépendants. Ceux-ci sont utilisés pour produire de deux ou plusieurs fichiers .tlb et éventuellement de les lier dans le bloc de ressources. Ce scénario n’est pas pris en charge dans Visual C++.  
  
 En outre, l’éditeur de liens Visual C++ génère toutes les informations d’attribut IDL en un seul fichier MIDL. Il n’y a aucun moyen de générer deux bibliothèques de types à partir d’un seul projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../windows/attributed-programming-concepts.md)