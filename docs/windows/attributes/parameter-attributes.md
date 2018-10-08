---
title: Attributs de paramètre (COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], parameter attributes
- parameter attributes
ms.assetid: 024c2dd5-49d7-4ced-a17a-c56c1bc485b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 160e71111a9080367390302a59c41a53580ffe0b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790641"
---
# <a name="parameter-attributes"></a>Attributs de paramètres

Les attributs suivants s’appliquent aux paramètres d’une méthode dans une classe ou interface.

|Attribut|Description|
|---------------|-----------------|
|[custom](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[defaultvalue](defaultvalue.md)|Permet de spécifier une valeur par défaut pour un paramètre facultatif typé.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[iid_is](iid-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[immediatebind](immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|
|[in](in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[lcid](lcid.md)|Vous permet de passer un identificateur de paramètres régionaux à une fonction.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[max_is](max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[Facultatif](optional-cpp.md)|Spécifie un paramètre facultatif pour une fonction membre.|
|[out](out-cpp.md)|Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[retval](retval.md)|Désigne le paramètre qui reçoit la valeur de retour du membre.|
|[satype](satype.md)|Spécifie le type de données de la `SAFEARRAY` structure.|
|[size_is](size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)