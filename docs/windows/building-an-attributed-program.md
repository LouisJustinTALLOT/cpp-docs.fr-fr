---
title: Générer un programmes par attributs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files [C++]
- MIDL
- MIDL, linker output
- IDL files [C++]
- building type libraries and .idl files
- .tlb files [C++]
- .idl files [C++]
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2fc148478433106eabdb2bc57ef7bb6c91d13601
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315288"
---
# <a name="building-an-attributed-program"></a>Générer un programmes par attributs

Une fois que vous placez des attributs Visual C++ dans votre code source, vous souhaiterez peut-être le compilateur Visual C++ pour générer un fichier de bibliothèque et .idl de type pour vous. Des options de l’éditeur de liens suivant vous aident à générer des fichiers .tlb et .idl :

- [OPTION /IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

Certains projets contiennent plusieurs fichiers .idl indépendants. Ceux-ci sont utilisés pour produire deux ou plusieurs fichiers .tlb et éventuellement de les lier dans le bloc de ressources. Ce scénario n’est pas pris en charge dans Visual C++.

En outre, l’éditeur de liens Visual C++ génère toutes les informations d’attributs IDL pour un seul fichier MIDL. Il n’y aura aucun moyen de générer deux bibliothèques de types à partir d’un projet unique.

## <a name="see-also"></a>Voir aussi

[Concepts](../windows/attributed-programming-concepts.md)