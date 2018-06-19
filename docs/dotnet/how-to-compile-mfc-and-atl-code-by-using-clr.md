---
title: 'Comment : compiler du Code MFC et ATL à l’aide de clr-| Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7412d69230bcb6375a042d6cf8e8f27a3d9eac9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136065"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Comment : compiler du code MFC et ATL à l'aide de /clr
Cette rubrique explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Pour compiler un fichier exécutable ou régulière MFC DLL MFC à l’aide de /clr  
  
1.  Cliquez sur le projet dans **l’Explorateur de solutions** puis cliquez sur **propriétés**.  
  
2.  Dans le **propriétés du projet** boîte de dialogue, développez le nœud à côté **propriétés de Configuration** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, définissez **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.  
  
     Dans le même volet, assurez-vous que **utilisation des MFC** a la valeur **utiliser les MFC dans une DLL partagée**.  
  
3.  Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Assurez-vous que **Format des informations de débogage** a la valeur **/Zi de base de données de programme** (pas **/Zi**).  
  
4.  Sélectionnez le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.  
  
5.  Sous **propriétés de Configuration**, sélectionnez **C/C++** , puis **génération de Code**. Assurez-vous que **de la bibliothèque Runtime** a la valeur **DLL de débogage multithread (/ MDd)** ou **DLL multithread (/ MD)**.  
  
6.  Dans le fichier Stdafx.h, ajoutez la ligne suivante.  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Pour compiler une DLL d’extension MFC à l’aide de /clr  
  
1.  Suivez les étapes décrites dans « To compiler un fichier exécutable ou régulière MFC DLL MFC à l’aide de /clr ».  
  
2.  Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **les en-têtes précompilés**. Définissez **Création/utilisation d’un en-tête précompilé** à **ne pas à l’aide d’en-têtes précompilés**.  
  
     En guise d’alternative, dans **l’Explorateur de solutions**, avec le bouton droit Stdafx.cpp, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **prise en charge non Common Language Runtime**.  
  
3.  Pour le fichier qui contient DllMain et tout ce qu’il appelle, en **l’Explorateur de solutions**, cliquez sur le fichier, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, définissez **compiler avec prise en charge du Common Language Runtime** à **prise en charge non Common Language Runtime**.  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>Pour compiler un exécutable ATL à l’aide de /clr  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet, puis sur **propriétés**.  
  
2.  Dans le **propriétés du projet** boîte de dialogue, développez le nœud à côté **propriétés de Configuration** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, définissez **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.  
  
3.  Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Assurez-vous que **Format des informations de débogage** a la valeur **/Zi de base de données de programme** (pas **/Zi**).  
  
4.  Sélectionnez le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.  
  
5.  Sous **propriétés de Configuration**, sélectionnez **C/C++** , puis **génération de Code**. Assurez-vous que **de la bibliothèque Runtime** a la valeur **DLL de débogage multithread (/ MDd)** ou **DLL multithread (/ MD)**.  
  
6.  Pour chaque fichier généré par MIDL (fichiers C), cliquez sur le fichier dans **l’Explorateur de solutions** puis cliquez sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **prise en charge non Common Language Runtime**.  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>Pour compiler une DLL ATL à l’aide de /clr  
  
1.  Suivez les étapes décrites dans la section « pour compiler un exécutable ATL à l’aide de /clr ».  
  
2.  Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **les en-têtes précompilés**. Définissez **Création/utilisation d’un en-tête précompilé** à **ne pas à l’aide d’en-têtes précompilés**.  
  
     En guise d’alternative, dans **l’Explorateur de solutions**, avec le bouton droit Stdafx.cpp, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Définissez **compiler avec prise en charge du Common Language Runtime** à **prise en charge non Common Language Runtime**.  
  
3.  Pour le fichier qui contient DllMain et tout ce qu’il appelle, en **l’Explorateur de solutions**, cliquez sur le fichier, puis sur **propriétés**. Sous **propriétés de Configuration**, développez le nœud à côté **C/C++** et sélectionnez **général**. Dans le volet droit, sous **projet par défaut est**, définissez **compiler avec prise en charge du Common Language Runtime** à **prise en charge non Common Language Runtime**.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)