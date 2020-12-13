---
description: 'En savoir plus sur les attributs suivants : Stand-Alone'
title: Attributs Stand-Alone (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 39b7356243f9b6ba7c42e907ca0733f59b85961e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329595"
---
# <a name="stand-alone-attributes"></a>Attributs autonomes

Un attribut autonome ne fonctionne pas sur un mot clé C++, mais ressemble davantage à une ligne de code. Les instructions d’attribut autonome requièrent un point-virgule à la fin de la ligne.

## <a name="stand-alone-attribute-list"></a>Liste des attributs autonomes

|Attribut|Description|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemets, dans le fichier d’en-tête généré.|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivants seront traités et placés dans le fichier. idl généré.|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des constructions IDL qui ne sont pas prises en charge dans la version actuelle de Visual C++ et de les transmettre au fichier. idl généré.|
|[import](import.md)|Spécifie un autre fichier. idl,. ODL ou. h contenant les définitions que vous souhaitez référencer à partir de votre fichier main. idl.|
|[importidl](importidl.md)|Insère le fichier. idl spécifié dans le fichier. idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[inclusion](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier. idl généré.|
|[includelib (](includelib-cpp.md)|Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[modules](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les guillemets, dans le fichier. idl généré.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)
