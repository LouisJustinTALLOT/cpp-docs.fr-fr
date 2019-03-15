---
title: Importation et exportation
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 882010cd28c291e9f49ca0f7dd9d646c70130184
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815825"
---
# <a name="importing-and-exporting"></a>Importation et exportation

Vous pouvez importer des symboles publics dans une application ou exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :

- Utiliser un fichier de définition (.def) de module lors de la génération de la DLL

- Utiliser les mots clés **__declspec (dllimport)** ou **__declspec (dllexport)** dans une définition de fonction dans l’application principale

## <a name="using-a-def-file"></a>À l’aide d’un fichier .def

Un fichier de définition de module (.def) est un fichier texte contenant une ou plusieurs instructions du module décrivant divers attributs d’une DLL. Si vous n’utilisez pas **__declspec (dllimport)** ou **__declspec (dllexport)** pour exporter des fonctions d’une DLL, la DLL exige un fichier .def.

Vous pouvez utiliser des fichiers .def pour [importer dans une application](importing-using-def-files.md) ou [exporter à partir d’une DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>À l’aide de __declspec

Visual C++ utilise **__declspec (dllimport)** et **__declspec (dllexport)** pour remplacer le **__export** mot clé utilisé précédemment dans les versions 16 bits de Visual C++.

Vous n’avez pas besoin d’utiliser **__declspec (dllimport)** pour votre code se compile correctement, mais cela permet au compilateur de générer un meilleur code. Le compilateur est en mesure de générer le code de meilleure qualité, car elle peut déterminer si une fonction existe dans une DLL ou non, ce qui permet au compilateur de générer le code qui ignore un niveau d’indirection qui serait normalement pas présente dans un appel de fonction qui ont franchi une limite de DLL. Toutefois, vous devez utiliser **__declspec (dllimport)** pour importer des variables utilisées dans une DLL.

Avec la section EXPORTS du fichier .def appropriée, **__declspec (dllexport)** n’est pas obligatoire. **__declspec (dllexport)** a été ajoutée pour fournir un moyen simple pour exporter des fonctions à partir d’un fichier .exe ou .dll sans utiliser un fichier .def.

Le format de fichier exécutable Portable Win32 est conçu pour réduire le nombre de pages qui doivent être impliqués pour réparer les importations. Pour ce faire, il place toutes les adresses d’importation pour n’importe quel programme dans un emplacement unique appelé Table des adresses d’importation. Ainsi, le chargeur modifier uniquement une ou deux pages lors de l’accès à ces importations.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Importer dans une Application](importing-into-an-application-using-declspec-dllimport.md)

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](dlls-in-visual-cpp.md)
