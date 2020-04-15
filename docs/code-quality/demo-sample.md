---
title: Exemple de projet C++ pour l’analyse du code
description: Comment créer une solution d’échantillon pour une utilisation dans l’analyse de code pas à pas pour Microsoft CMD dans Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372063"
---
# <a name="sample-c-project-for-code-analysis"></a>Exemple de projet C++ pour l’analyse du code

Les procédures suivantes vous montrent comment créer l’échantillon pour [Walkthrough: AnalyseZ le code C/C POUR les défauts](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Les procédures créent :

- Une solution Visual Studio nommée *CppDemo*.

- Un projet de bibliothèque statique nommé *CodeDefects*.

- Un projet de bibliothèque statique nommé *Annotations*.

Les procédures fournissent également le code pour les fichiers d’en-tête et *.cpp* pour les bibliothèques statiques.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Créer la solution CppDemo et le projet CodeDefects

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio et sélectionnez **Créer un nouveau projet**

1. Dans le **dialogue Créer un nouveau projet,** changer le filtre de langue en C **.**

1. Sélectionnez **Windows Desktop Wizard** et choisissez le bouton **Suivant.**

1. Sur la configuration de votre nouvelle page **de projet,** dans la boîte de texte nom **du projet,** entrez *CodeDefects*.

1. Dans la boîte de **texte nom de solution,** entrez *CppDemo*.

1. Cliquez sur **Créer**.

1. Dans le dialogue **windows Desktop Project,** modifiez le **type d’application** en **Bibliothèque statique (.lib)**.

1. Sous **Options supplémentaires**, sélectionnez **Projet vide**.

1. Choisissez **OK** pour créer la solution et le projet.

::: moniker-end

::: moniker range="vs-2017"

1. Ouvrez Visual Studio. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans le dialogue du **nouveau projet,** sélectionnez **Visual CMD** > **Windows Desktop**.

1. Sélectionnez **Windows Desktop Wizard**.

1. Dans la boîte à texte **Nom,** entrez *CodeDefects*.

1. Dans la boîte de **texte nom de solution,** entrez *CppDemo*.

1. Choisissez **OK**.

1. Dans le dialogue **windows Desktop Project,** modifiez le **type d’application** en **Bibliothèque statique (.lib)**.

1. Sous **Options supplémentaires**, sélectionnez **Projet vide**.

1. Choisissez **OK** pour créer la solution et le projet.

::: moniker-end

::: moniker range="vs-2015"

1. Ouvrez Visual Studio. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans le dialogue du **nouveau projet,** sélectionnez **Templates** > **Visual CMMD** > **Win32**.

1. Sélectionnez **Win32 Console Application**.

1. Dans la boîte à texte **Nom,** entrez *CodeDefects*.

1. Dans la boîte de **texte nom de solution,** entrez *CppDemo*.

1. Choisissez **OK**.

1. Dans le dialogue **Win32 Application Wizard,** choisissez le bouton **Suivant.**

1. Modifier le **type d’application** en **bibliothèque statique**.

1. En vertu **d’options supplémentaires**, unselect **En-tête précompilé**.

1. Choisissez **Finition** pour créer la solution et le projet.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Ajouter le fichier source et d’en-tête au projet CodeDefects

1. Dans Solution Explorer, étendre **CodeDefects**.

1. Cliquez à droite pour ouvrir le menu contextuelle pour **header Files**. Choisissez **Ajouter un** > **nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **Visual CMD** > **Code**, puis sélectionnez Header **File (.h)**.

1. Dans la boîte **d’édition Nom,** entrez *Bug.h*, puis choisissez le bouton **Ajouter.**

1. Dans la fenêtre d’édition pour *Bug.h*, sélectionnez et supprimez le contenu.

1. Copiez le code suivant et collez-le dans le fichier *Bug.h* dans l’éditeur.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. Dans Solution Explorer, cliquez à droite pour ouvrir le menu contextuelle des **fichiers Source**. Choisissez **Ajouter un** > **nouvel article**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**.

1. Dans la boîte **d’édition Nom,** entrez *Bug.cpp,* puis choisissez le bouton **Ajouter.**

1. Copiez le code suivant et collez-le dans le fichier *Bug.cpp* dans l’éditeur.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. Sur la barre de menu, choisissez **File** > **Save All**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ajouter le projet Annotations et le configurer comme bibliothèque statique

::: moniker range=">=vs-2019"

1. Dans Solution Explorer, cliquez à droite **CppDemo** pour ouvrir le menu context. Choisissez **Ajouter** > **un nouveau projet**.

1. Dans **l’ajouter une nouvelle** boîte de dialogue de projet, sélectionnez **Windows Desktop Wizard,** puis choisissez le bouton **Suivant.**

1. Sur la configuration de votre nouvelle page **de projet,** dans la boîte de **texte nom du projet,** entrez *Annotations*, puis choisissez **Créer**.

1. Dans le dialogue **windows Desktop Project,** modifiez le **type d’application** en **Bibliothèque statique (.lib)**.

1. Sous **Options supplémentaires**, sélectionnez **Projet vide**.

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

1. Dans Solution Explorer, cliquez à droite **CppDemo** pour ouvrir le menu context. Choisissez **Ajouter** > **un nouveau projet**.

1. Dans le dialogue **Add New Project,** sélectionnez **Visual CMD** > **Windows Desktop**.

1. Sélectionnez **Windows Desktop Wizard**.

1. Dans la boîte de texte **Nom,** entrez *Annotations*, puis choisissez **OK**.

1. Dans le dialogue **windows Desktop Project,** modifiez le **type d’application** en **Bibliothèque statique (.lib)**.

1. Sous **Options supplémentaires**, sélectionnez **Projet vide**.

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

1. Dans Solution Explorer, cliquez à droite **CppDemo** pour ouvrir le menu context. Choisissez **Ajouter** > **un nouveau projet**.

1. Dans le dialogue **Add New Project,** sélectionnez **Visual CMD** > **Win32**.

1. Sélectionnez **Win32 Console Application**.

1. Dans la boîte à texte **Nom,** entrez *Annotations*.

1. Choisissez **OK**.

1. Dans le dialogue **Win32 Application Wizard,** choisissez le bouton **Suivant.**

1. Modifier le **type d’application** en **bibliothèque statique**.

1. En vertu **d’options supplémentaires**, unselect **En-tête précompilé**.

1. Choisissez **Finition** pour créer le projet.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Ajouter le fichier d’en-tête et le fichier source au projet Annotations

1. Dans Solution Explorer, étendre **Annotations**.

1. Cliquez à droite pour ouvrir le menu contextuelle des **fichiers d’en-tête** sous **Annotations**. Choisissez **Ajouter un** > **nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **Visual CMD** > **Code**, puis sélectionnez Header **File (.h)**.

1. Dans la boîte **d’édition Nom,** entrez *annotations.h*, puis choisissez le bouton **Ajouter.**

1. Dans la fenêtre *d’édition pour annotations.h*, sélectionnez et supprimez le contenu.

1. Copiez le code suivant et collez-le dans le fichier *annotations.h* dans l’éditeur.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. Dans Solution Explorer, cliquez à droite pour ouvrir le menu contextuelle des **fichiers Source** sous **Annotations**. Choisissez **Ajouter un** > **nouvel article**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)**.

1. Dans la boîte **d’édition Nom,** entrez *annotations.cpp*, puis choisissez le bouton **Ajouter.**

1. Copiez le code suivant et collez-le dans le fichier *annotations.cpp* dans l’éditeur.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. Sur la barre de menu, choisissez **File** > **Save All**.

La solution est maintenant terminée et devrait être construite sans erreurs.

::: moniker range="vs-2017"

> [!NOTE]
> Dans Visual Studio 2017, vous pouvez `E1097 unknown attribute "no_init_all"` voir un avertissement fallacieux dans le moteur IntelliSense. Vous pouvez ignorer cet avertissement sans problème.

::: moniker-end
