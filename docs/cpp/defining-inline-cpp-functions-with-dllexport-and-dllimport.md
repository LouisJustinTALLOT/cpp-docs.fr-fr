---
title: Définition de fonctions C++ incorporées avec dllexport et dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 9620706e6ac477246ce323a7fc3624291bb1dd6b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180197"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Définition de fonctions C++ incorporées avec dllexport et dllimport

**Section spécifique de Microsoft**

Vous pouvez définir comme Inline une fonction avec l’attribut **dllexport** . Dans ce cas, la fonction est toujours instanciée et exportée, qu'elle soit référencée ou non par un module du programme. La fonction est présumée être importée par un autre programme.

Vous pouvez également définir comme inline une fonction déclarée avec l'attribut **dllimport**. Dans ce cas, la fonction peut être développée (soumise aux spécifications /Ob) mais jamais instanciée. En particulier, si l'adresse d'une fonction importée inline est reçue, l'adresse de la fonction résidant dans la DLL est retournée. Ce comportement est identique à la réception de l'adresse d'une fonction importée non inline.

Ces règles s'appliquent aux fonctions inline dont les définitions apparaissent dans une définition de classe. De plus, les données locales statiques et les chaînes des fonctions inline conservent les mêmes identités entre la DLL et le client qu'elles le feraient dans un programme unique (autrement dit un fichier exécutable sans interface DLL).

Soyez vigilant en fournissant des fonctions inline importées. Par exemple, si vous mettez à jour la DLL, ne supposez pas que le client utilisera sa version modifiée. Pour vous assurer que vous chargez la version appropriée de la DLL, régénérez aussi le client de la DLL.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
