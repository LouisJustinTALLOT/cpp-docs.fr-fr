---
description: 'En savoir plus sur : Comment : compiler du code MFC et ATL à l’aide de/CLR'
title: 'Comment : compiler du code MFC et ATL à l’aide de-CLR'
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
ms.openlocfilehash: 67a861dac3b4c4b454f4fbde4a500c3677ce0e25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304491"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Comment : compiler du code MFC et ATL à l'aide de /clr

Cette rubrique explique comment compiler des programmes MFC et ATL existants pour cibler le Common Language Runtime.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Pour compiler une DLL MFC exécutable ou standard à l’aide de/CLR

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

1. Dans la boîte de dialogue **Propriétés du projet** , développez le nœud en regard de **Propriétés de configuration** et sélectionnez **général**. Dans le volet droit, sous **paramètres par défaut du projet**, définissez prise en charge du Common **Language Runtime** pour la **prise en charge du Common Language Runtime (/CLR)**.

   Dans le même volet, assurez-vous que l' **utilisation de MFC** est définie pour **utiliser MFC dans une DLL partagée**.

1. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Assurez-vous que le **format des informations de débogage** est défini sur **programmer la base de données/Zi** (et non **/Zi**).

1. Sélectionnez le nœud **génération de code** . Affectez à **activer la régénération minimale** la valeur **non (/GM-)**. Affectez également la valeur **par défaut** aux **vérifications de base du runtime** .

1. Sous **Propriétés de configuration**, sélectionnez **C/C++** , puis **génération de code**. Vérifiez que la **bibliothèque Runtime** est définie sur **dll de débogage multithread (/MDD)** ou **DLL multithread (/MD)**.

1. Dans stdafx. h, ajoutez la ligne suivante.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Pour compiler une DLL d’extension MFC à l’aide de/CLR

1. Suivez les étapes de la section « pour compiler un fichier exécutable MFC ou une DLL MFC normale à l’aide de/CLR ».

1. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **en-têtes précompilés**. Définissez **créer/utiliser un en-tête précompilé** pour **ne pas utiliser les en-têtes précompilés**.

   En guise d’alternative, dans **Explorateur de solutions**, cliquez avec le bouton droit sur stdafx. cpp, puis cliquez sur **Propriétés**. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Définir la **compilation avec prise en charge du Common Language Runtime** pour **ne pas prendre en charge le Common Language Runtime**.

1. Pour le fichier qui contient DllMain et tout ce qu’il appelle, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier, puis cliquez sur **Propriétés**. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Dans le volet droit, sous **paramètres par défaut du projet**, définissez **compilation avec prise en charge du Common Language Runtime** sur **aucune prise en charge du Common Language Runtime**.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>Pour compiler un exécutable ATL à l’aide de/CLR

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

1. Dans la boîte de dialogue **Propriétés du projet** , développez le nœud en regard de **Propriétés de configuration** et sélectionnez **général**. Dans le volet droit, sous **paramètres par défaut du projet**, définissez prise en charge du Common **Language Runtime** pour la **prise en charge du Common Language Runtime (/CLR)**.

1. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Assurez-vous que le **format des informations de débogage** est défini sur **programmer la base de données/Zi** (et non **/Zi**).

1. Sélectionnez le nœud **génération de code** . Affectez à **activer la régénération minimale** la valeur **non (/GM-)**. Affectez également la valeur **par défaut** aux **vérifications de base du runtime** .

1. Sous **Propriétés de configuration**, sélectionnez **C/C++** , puis **génération de code**. Vérifiez que la **bibliothèque Runtime** est définie sur **dll de débogage multithread (/MDD)** ou **DLL multithread (/MD)**.

1. Pour chaque fichier généré par MIDL (fichiers C), cliquez avec le bouton droit sur le fichier dans **Explorateur de solutions** puis cliquez sur **Propriétés**. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Définir la **compilation avec prise en charge du Common Language Runtime** pour **ne pas prendre en charge le Common Language Runtime**.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>Pour compiler une DLL ATL à l’aide de/CLR

1. Suivez les étapes de la section « pour compiler un exécutable ATL à l’aide de/CLR ».

1. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **en-têtes précompilés**. Définissez **créer/utiliser un en-tête précompilé** pour **ne pas utiliser les en-têtes précompilés**.

   En guise d’alternative, dans **Explorateur de solutions**, cliquez avec le bouton droit sur stdafx. cpp, puis cliquez sur **Propriétés**. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Définir la **compilation avec prise en charge du Common Language Runtime** pour **ne pas prendre en charge le Common Language Runtime**.

1. Pour le fichier qui contient DllMain et tout ce qu’il appelle, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier, puis cliquez sur **Propriétés**. Sous **Propriétés de configuration**, développez le nœud en regard de **C/C++** , puis sélectionnez **général**. Dans le volet droit, sous **paramètres par défaut du projet**, définissez **compilation avec prise en charge du Common Language Runtime** sur **aucune prise en charge du Common Language Runtime**.

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
