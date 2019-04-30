---
title: Attributs autonomes (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 7dd1f35add3b23dbd81e32a1600481eec79fe7d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407261"
---
# <a name="stand-alone-attributes"></a>Attributs autonomes

Un attribut autonome ne fonctionne pas sur un mot clé C++, mais plutôt d’une ligne de code. Les instructions d’attribut autonome nécessitent un point-virgule à la fin de la ligne.

## <a name="stand-alone-attribute-list"></a>Liste d’attributs autonomes

|Attribut|Description|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier d’en-tête généré.|
|[custom](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivantes seront traitées et placés dans le fichier .idl généré.|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des constructions IDL qui ne sont pas pris en charge dans la version actuelle de Visual C++ et les passer au fichier .idl généré.|
|[import](import.md)|Spécifie un autre fichier .idl et .h .odl contenant les définitions que vous souhaitez référencer à partir de votre fichier .idl principal.|
|[importidl](importidl.md)|Insère le fichier .idl spécifié dans le fichier .idl généré|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[include](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.|
|[includelib](includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[module](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)