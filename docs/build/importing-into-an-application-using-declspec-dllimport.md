---
title: Importer dans une application à l’aide de __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440407"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>Importer dans une application à l’aide de __declspec(dllimport)

Un programme qui utilise des symboles publics définis par une DLL est dit de les importer. Lorsque vous créez des fichiers d’en-tête pour les applications qui utilisent vos dll pour la génération avec, utilisez **__declspec (dllimport)** sur les déclarations des symboles publics. Le mot clé **__declspec (dllimport)** fonctionne que vous exportez avec des fichiers. def ou avec le mot clé **__declspec (dllexport)** .

Pour rendre votre code plus lisible, définissez une macro pour **__declspec (dllimport)** , puis utilisez la macro pour déclarer chaque symbole importé :

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

L’utilisation de **__declspec (dllimport)** est facultative dans les déclarations de fonction, mais le compilateur produit un code plus efficace si vous utilisez ce mot clé. Toutefois, vous devez utiliser **__declspec (dllimport)** pour l’exécutable d’importation pour accéder aux symboles et objets de données publics de la dll. Notez que les utilisateurs de votre DLL doivent toujours établir une liaison avec une bibliothèque d’importation.

Vous pouvez utiliser le même fichier d’en-tête pour la DLL et l’application cliente. Pour ce faire, utilisez un symbole de préprocesseur spécial qui indique si vous générez la DLL ou si vous générez l’application cliente. Par exemple :

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Importation dans une application](importing-into-an-application.md)
