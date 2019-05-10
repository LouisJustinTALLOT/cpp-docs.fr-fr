---
title: Importation et exportation
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220640"
---
# <a name="importing-and-exporting"></a>Importation et exportation

Vous pouvez importer des symboles publics dans une application ou exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :

- Utiliser un fichier de définition (.def) de module lors de la génération de la DLL

- Utiliser les mots clés **__declspec (dllimport)** ou **__declspec (dllexport)** dans une définition de fonction dans l’application principale

## <a name="using-a-def-file"></a>À l’aide d’un fichier .def

Un fichier de définition de module (.def) est un fichier texte contenant une ou plusieurs instructions du module décrivant divers attributs d’une DLL. Si vous n’utilisez pas **__declspec (dllimport)** ou **__declspec (dllexport)** pour exporter des fonctions d’une DLL, la DLL exige un fichier .def.

Vous pouvez utiliser des fichiers .def pour [importer dans une application](importing-using-def-files.md) ou [exporter à partir d’une DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>À l’aide de __declspec

Vous n’avez pas besoin d’utiliser **__declspec (dllimport)** pour votre code se compile correctement, mais cela permet au compilateur de générer un meilleur code. Le compilateur est en mesure de générer le code de meilleure qualité, car elle peut déterminer si une fonction existe dans une DLL ou non, ce qui permet au compilateur de générer le code qui ignore un niveau d’indirection qui serait normalement pas présente dans un appel de fonction qui ont franchi une limite de DLL. Toutefois, vous devez utiliser **__declspec (dllimport)** pour importer des variables utilisées dans une DLL.

Avec la section EXPORTS du fichier .def appropriée, **__declspec (dllexport)** n’est pas obligatoire. **__declspec (dllexport)** a été ajoutée pour fournir un moyen simple pour exporter des fonctions à partir d’un fichier .exe ou .dll sans utiliser un fichier .def.

Le format de fichier exécutable Portable Win32 est conçu pour réduire le nombre de pages qui doivent être impliqués pour réparer les importations. Pour ce faire, il place toutes les adresses d’importation pour n’importe quel programme dans un emplacement unique appelé Table des adresses d’importation. Ainsi, le chargeur modifier uniquement une ou deux pages lors de l’accès à ces importations.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Importer dans une Application](importing-into-an-application-using-declspec-dllimport.md)

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Voir aussi

[Créer des DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
