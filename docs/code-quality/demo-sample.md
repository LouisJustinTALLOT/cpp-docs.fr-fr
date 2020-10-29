---
title: Exemple de projet C++ pour l’analyse du code
description: Comment créer un exemple de solution à utiliser dans la procédure pas à pas relative à l’analyse du code pour Microsoft C++ dans Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: dd4fe67c05200ccc2865bc7c48b1f5047d77565e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924624"
---
# <a name="sample-c-project-for-code-analysis"></a>Exemple de projet C++ pour l’analyse du code

Les procédures suivantes vous montrent comment créer l’exemple pour la [procédure pas à pas : analyse du code C/C++ pour les défauts](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Les procédures créent :

- Une solution Visual Studio nommée *CppDemo* .

- Un projet de bibliothèque statique nommé *CodeDefects* .

- Un projet de bibliothèque statique nommé *Annotations* .

Les procédures fournissent également le code pour les fichiers d’en-tête et *.cpp* pour les bibliothèques statiques.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Créer la solution CppDemo et le projet CodeDefects

::: moniker range=">=msvc-160"

1. Ouvrez Visual Studio et sélectionnez **créer un nouveau projet**

1. Dans la boîte de dialogue **créer un nouveau projet** , modifiez le filtre de langage en **C++** .

1. Sélectionnez **Assistant du bureau Windows** , puis choisissez le bouton **suivant** .

1. Dans la page **configurer votre nouveau projet** , dans la zone de texte **nom du projet** , entrez *CodeDefects* .

1. Dans la zone de texte nom de la **solution** , entrez *CppDemo* .

1. Choisissez **Créer** .

1. Dans la boîte de dialogue **projet de bureau Windows** , modifiez le **type d’application** en **bibliothèque statique (. lib)** .

1. Sous **Options supplémentaires** , sélectionnez **Projet vide** .

1. Choisissez **OK** pour créer la solution et le projet.

::: moniker-end

::: moniker range="msvc-150"

1. Ouvrez Visual Studio. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** .

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C++** > **Bureau Windows** .

1. Sélectionnez **Assistant du bureau Windows** .

1. Dans la zone de texte **nom** , entrez *CodeDefects* .

1. Dans la zone de texte nom de la **solution** , entrez *CppDemo* .

1. Choisissez **OK** .

1. Dans la boîte de dialogue **projet de bureau Windows** , modifiez le **type d’application** en **bibliothèque statique (. lib)** .

1. Sous **Options supplémentaires** , sélectionnez **Projet vide** .

1. Choisissez **OK** pour créer la solution et le projet.

::: moniker-end

::: moniker range="msvc-140"

1. Ouvrez Visual Studio. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** .

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **modèles** > **Visual C++** > **Win32** .

1. Sélectionnez **application console Win32** .

1. Dans la zone de texte **nom** , entrez *CodeDefects* .

1. Dans la zone de texte nom de la **solution** , entrez *CppDemo* .

1. Choisissez **OK** .

1. Dans la boîte de dialogue de l' **Assistant application Win32** , choisissez le bouton **suivant** .

1. Remplacez le **type d’application** par **bibliothèque statique** .

1. Sous **options supplémentaires** , désélectionnez l' **en-tête précompilé** .

1. Choisissez **Terminer** pour créer la solution et le projet.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Ajouter le fichier source et d’en-tête au projet CodeDefects

1. Dans Explorateur de solutions, développez **CodeDefects** .

1. Cliquez avec le bouton droit pour ouvrir le menu contextuel des **fichiers d’en-tête** . Choisissez **Ajouter**  >  **un nouvel élément** .

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++**  >  **code** , puis sélectionnez **fichier d’en-tête (. h)** .

1. Dans la zone d’édition **nom** , entrez *bug. h* , puis choisissez le bouton **Ajouter** .

1. Dans la fenêtre d’édition de *bug. h* , sélectionnez et supprimez le contenu.

1. Copiez le code suivant et collez-le dans le fichier *bug. h* dans l’éditeur.

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

1. Dans Explorateur de solutions, cliquez avec le bouton droit pour ouvrir le menu contextuel des **fichiers sources** . Choisissez **Ajouter**  >  **un nouvel élément** .

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)** .

1. Dans la zone d’édition **nom** , entrez *bug. cpp* , puis cliquez sur le bouton **Ajouter** .

1. Copiez le code suivant et collez-le dans le fichier *bug. cpp* dans l’éditeur.

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

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout** .

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ajouter le projet Annotations et le configurer comme bibliothèque statique

::: moniker range=">=msvc-160"

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur **CppDemo** pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  **un nouveau projet** .

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez **Assistant du bureau Windows** , puis cliquez sur le bouton **suivant** .

1. Dans la page **configurer votre nouveau projet** , dans la zone de texte **nom du projet** , entrez *Annotations* , puis choisissez **créer** .

1. Dans la boîte de dialogue **projet de bureau Windows** , modifiez le **type d’application** en **bibliothèque statique (. lib)** .

1. Sous **Options supplémentaires** , sélectionnez **Projet vide** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="msvc-150"

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur **CppDemo** pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  **un nouveau projet** .

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez **Visual C++** > **Bureau Windows** .

1. Sélectionnez **Assistant du bureau Windows** .

1. Dans la zone de texte **nom** , entrez *Annotations* , puis choisissez **OK** .

1. Dans la boîte de dialogue **projet de bureau Windows** , modifiez le **type d’application** en **bibliothèque statique (. lib)** .

1. Sous **Options supplémentaires** , sélectionnez **Projet vide** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="msvc-140"

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur **CppDemo** pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  **un nouveau projet** .

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez **Visual C++** > **Win32** .

1. Sélectionnez **application console Win32** .

1. Dans la zone de texte **nom** , entrez *Annotations* .

1. Choisissez **OK** .

1. Dans la boîte de dialogue de l' **Assistant application Win32** , choisissez le bouton **suivant** .

1. Remplacez le **type d’application** par **bibliothèque statique** .

1. Sous **options supplémentaires** , désélectionnez l' **en-tête précompilé** .

1. Choisissez **Terminer** pour créer le projet.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Ajouter le fichier d’en-tête et le fichier source au projet Annotations

1. Dans Explorateur de solutions, développez **Annotations** .

1. Cliquez avec le bouton droit pour ouvrir le menu contextuel des **fichiers d’en-tête** sous **Annotations** . Choisissez **Ajouter**  >  **un nouvel élément** .

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++**  >  **code** , puis sélectionnez **fichier d’en-tête (. h)** .

1. Dans la zone d’édition **nom** , entrez *Annotations. h* , puis choisissez le bouton **Ajouter** .

1. Dans la fenêtre Modifier pour *Annotations. h* , sélectionnez et supprimez le contenu.

1. Copiez le code suivant et collez-le dans le fichier *Annotations. h* dans l’éditeur.

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

1. Dans Explorateur de solutions, cliquez avec le bouton droit pour ouvrir le menu contextuel des **fichiers sources** sous **Annotations** . Choisissez **Ajouter**  >  **un nouvel élément** .

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier C++ (.cpp)** .

1. Dans la zone d’édition **nom** , entrez *Annotations. cpp* , puis cliquez sur le bouton **Ajouter** .

1. Copiez le code suivant et collez-le dans le fichier *Annotations. cpp* dans l’éditeur.

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

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout** .

La solution est maintenant terminée et doit être générée sans erreurs.

::: moniker range="msvc-150"

> [!NOTE]
> Dans Visual Studio 2017, vous pouvez voir un avertissement parasite `E1097 unknown attribute "no_init_all"` dans le moteur IntelliSense. Vous pouvez ignorer cet avertissement sans problème.

::: moniker-end
