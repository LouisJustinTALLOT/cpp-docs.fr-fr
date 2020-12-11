---
description: 'En savoir plus sur : importation et exportation'
title: Importation et exportation
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: e2045b41450881056fb109f059e9c3202d93cab3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162519"
---
# <a name="importing-and-exporting"></a>Importation et exportation

Vous pouvez importer des symboles publics dans une application ou exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :

- Utiliser un fichier de définition de module (. def) lors de la génération de la DLL

- Utiliser les mots clés **`__declspec(dllimport)`** ou **`__declspec(dllexport)`** dans une définition de fonction dans l’application principale

## <a name="using-a-def-file"></a>Utilisation d’un fichier. def

Un fichier de définition de module (. def) est un fichier texte contenant une ou plusieurs instructions de module qui décrivent différents attributs d’une DLL. Si vous n’utilisez pas **`__declspec(dllimport)`** ou **`__declspec(dllexport)`** pour exporter les fonctions d’une dll, la dll requiert un fichier. def.

Vous pouvez utiliser des fichiers. def pour [importer dans une application](importing-using-def-files.md) ou pour effectuer [une exportation à partir d’une dll](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>Utilisation de __declspec

Vous n’avez pas besoin d’utiliser **`__declspec(dllimport)`** pour que votre code se compile correctement, mais cela permet au compilateur de générer un meilleur code. Le compilateur est en mesure de générer un meilleur code, car il peut déterminer si une fonction existe dans une DLL ou non, ce qui permet au compilateur de produire du code qui ignore un niveau d’indirection qui serait normalement présent dans un appel de fonction qui franchit une limite de DLL. Toutefois, vous devez utiliser **`__declspec(dllimport)`** pour importer des variables utilisées dans une dll.

La section EXPORTS de fichier. def appropriée **`__declspec(dllexport)`** n’est pas obligatoire. **`__declspec(dllexport)`** a été ajouté pour fournir un moyen simple d’exporter des fonctions à partir d’un fichier. exe ou. dll sans utiliser de fichier. def.

Le format exécutable portable Win32 est conçu pour réduire le nombre de pages qui doivent être touchées pour corriger les importations. Pour ce faire, il place toutes les adresses d’importation d’un programme à un emplacement appelé table d’adresses d’importation. Cela permet au chargeur de modifier une ou deux pages uniquement lors de l’accès à ces importations.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Importer dans une application](importing-into-an-application-using-declspec-dllimport.md)

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
