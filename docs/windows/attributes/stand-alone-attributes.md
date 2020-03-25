---
title: Attributs autonomes (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166167"
---
# <a name="stand-alone-attributes"></a>Attributs autonomes

Un attribut autonome ne fonctionne pas sur un C++ mot clé, mais ressemble davantage à une ligne de code. Les instructions d’attribut autonome requièrent un point-virgule à la fin de la ligne.

## <a name="stand-alone-attribute-list"></a>Liste des attributs autonomes

|Attribut|Description|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemets, dans le fichier d’en-tête généré.|
|[custom](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivants seront traités et placés dans le fichier. idl généré.|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des constructions IDL qui ne sont pas prises en charge dans la version C++ actuelle de Visual et de les transmettre au fichier. idl généré.|
|[import](import.md)|Spécifie un autre fichier. idl,. ODL ou. h contenant les définitions que vous souhaitez référencer à partir de votre fichier main. idl.|
|[importidl](importidl.md)|Insère le fichier. idl spécifié dans le fichier. idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[include](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier. idl généré.|
|[includelib](includelib-cpp.md)|Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[module](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les guillemets, dans le fichier. idl généré.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)
