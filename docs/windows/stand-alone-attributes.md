---
title: Attributs autonomes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c44223dad2ac4d6306bf3896cd8ec7be84a5a2b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407762"
---
# <a name="stand-alone-attributes"></a>Attributs autonomes
Un attribut autonome ne fonctionne pas sur un mot clé C++, mais plutôt d’une ligne de code. Les instructions d’attribut autonome nécessitent un point-virgule à la fin de la ligne.
  
|Attribut|Description|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier d’en-tête généré.|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|
|[emitidl](../windows/emitidl.md)|Détermine si tous les attributs IDL suivantes seront traitées et placés dans le fichier .idl généré.|
|[idl_module](../windows/idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](../windows/idl-quote.md)|Vous permet d’utiliser des constructions IDL qui ne sont pas pris en charge dans la version actuelle de Visual C++ et les passer au fichier .idl généré.|
|[import](../windows/import.md)|Spécifie un autre fichier .idl et .h .odl contenant les définitions que vous souhaitez référencer à partir de votre fichier .idl principal.|
|[importidl](../windows/importidl.md)|Insère le fichier .idl spécifié dans le fichier .idl généré|
|[importlib](../windows/importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[include](../windows/include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.|
|[includelib](../windows/includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[library_block](../windows/library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[module](../windows/module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[no_injected_text](../windows/no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|
|[pragma](../windows/pragma.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.|
  
## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](../windows/attributes-by-usage.md)