---
title: Définition de fonctions C++ incorporées avec dllexport et dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 39c1787321a37601cd8777ddb6c8296936eb89e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399003"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Définition de fonctions C++ incorporées avec dllexport et dllimport

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Vous pouvez définir comme inline une fonction avec la **dllexport** attribut. Dans ce cas, la fonction est toujours instanciée et exportée, qu'elle soit référencée ou non par un module du programme. La fonction est présumée être importée par un autre programme.

Vous pouvez également définir comme inline une fonction déclarée avec l'attribut **dllimport**. Dans ce cas, la fonction peut être développée (soumise aux spécifications /Ob) mais jamais instanciée. En particulier, si l'adresse d'une fonction importée inline est reçue, l'adresse de la fonction résidant dans la DLL est retournée. Ce comportement est identique à la réception de l'adresse d'une fonction importée non inline.

Ces règles s'appliquent aux fonctions inline dont les définitions apparaissent dans une définition de classe. De plus, les données locales statiques et les chaînes des fonctions inline conservent les mêmes identités entre la DLL et le client qu'elles le feraient dans un programme unique (autrement dit un fichier exécutable sans interface DLL).

Soyez vigilant en fournissant des fonctions inline importées. Par exemple, si vous mettez à jour la DLL, ne supposez pas que le client utilisera sa version modifiée. Pour vous assurer que vous chargez la version appropriée de la DLL, régénérez aussi le client de la DLL.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)