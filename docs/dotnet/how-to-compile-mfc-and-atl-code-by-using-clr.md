---
title: 'Procédure : Compiler le Code MFC et ATL à l’aide de - clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
ms.openlocfilehash: 9a24e82787eb0fce8ff668843e73de9f2d05e1ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379042"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Procédure : / CLR MFC et ATL Code à l’aide de la compilation

Cette rubrique explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Pour compiler un fichier exécutable ou régulière MFC DLL MFC à l’aide de /clr

1. Cliquez sur le projet dans **l’Explorateur de solutions** puis cliquez sur **propriétés**.

1. Dans le **propriétés du projet** boîte de dialogue, développez le nœud regard **propriétés de Configuration** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, affectez la valeur **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.

   Dans le même volet, assurez-vous que **utilisation des MFC** a la valeur **utiliser les MFC dans une DLL partagée**.

1. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Assurez-vous que l’option **Format des informations de débogage** a la valeur **/Zi de base de données de programme** (pas **/Zi**).

1. Sélectionnez le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.

1. Sous **propriétés de Configuration**, sélectionnez **C/C++** , puis **génération de Code**. Assurez-vous que l’option **bibliothèque Runtime** a la valeur **DLL de débogage multithread (/ MDd)** ou **DLL multithread (/ MD)**.

1. Dans Stdafx.h, ajoutez la ligne suivante.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Pour compiler une DLL d’extension MFC à l’aide de /clr

1. Suivez les étapes décrites dans « To compilez un exécutable ou régulière MFC DLL MFC à l’aide de /clr ».

1. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **en-têtes précompilés**. Définissez **Création/utilisation d’un en-tête précompilé** à **ne pas à l’aide d’en-têtes précompilés**.

   Comme alternative, dans **l’Explorateur de solutions**, avec le bouton droit Stdafx.cpp, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **non Common Language Runtime support**.

1. Pour le fichier qui contient DllMain et tout ce qu’il appelle, dans **l’Explorateur de solutions**, cliquez sur le fichier, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, affectez la valeur **compiler avec prise en charge du Common Language Runtime** à **non Common Language Runtime support**.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>Pour compiler un exécutable ATL à l’aide de /clr

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis cliquez sur **propriétés**.

1. Dans le **propriétés du projet** boîte de dialogue, développez le nœud regard **propriétés de Configuration** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, affectez la valeur **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.

1. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Assurez-vous que l’option **Format des informations de débogage** a la valeur **/Zi de base de données de programme** (pas **/Zi**).

1. Sélectionnez le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.

1. Sous **propriétés de Configuration**, sélectionnez **C/C++** , puis **génération de Code**. Assurez-vous que l’option **bibliothèque Runtime** a la valeur **DLL de débogage multithread (/ MDd)** ou **DLL multithread (/ MD)**.

1. Pour chaque fichier généré par MIDL (fichiers C), cliquez sur le fichier dans **l’Explorateur de solutions** puis cliquez sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **non Common Language Runtime support**.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>Pour compiler une DLL ATL à l’aide de /clr

1. Suivez les étapes décrites dans la section « pour compiler un exécutable ATL à l’aide de /clr ».

1. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **en-têtes précompilés**. Définissez **Création/utilisation d’un en-tête précompilé** à **ne pas à l’aide d’en-têtes précompilés**.

   Comme alternative, dans **l’Explorateur de solutions**, avec le bouton droit Stdafx.cpp, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **non Common Language Runtime support**.

1. Pour le fichier qui contient DllMain et tout ce qu’il appelle, dans **l’Explorateur de solutions**, cliquez sur le fichier, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud regard **C/C++** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, affectez la valeur **compiler avec prise en charge du Common Language Runtime** à **non Common Language Runtime support**.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
