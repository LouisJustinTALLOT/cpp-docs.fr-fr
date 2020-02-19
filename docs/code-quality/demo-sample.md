---
title: Exemple de projet C++ pour l’analyse du code
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: 1966e9cec5825ae37728bbf28c0f21ff4eed62fc
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418822"
---
# <a name="sample-c-project-for-code-analysis"></a>Exemple de projet C++ pour l’analyse du code

Les procédures suivantes vous montrent comment créer l’exemple pour la [procédure pas à pas :C++ analyser C/code pour les défauts](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Les procédures créent :

- Une solution Visual Studio nommée CppDemo.

- Un projet de bibliothèque statique nommé CodeDefects.

- Un projet de bibliothèque statique nommé Annotations.

Les procédures fournissent également le code pour les fichiers d’en-tête et *.cpp* pour les bibliothèques statiques.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Créer la solution CppDemo et le projet CodeDefects

1. Ouvrez Visual Studio et sélectionnez **créer un nouveau projet**

1. Changer le filtre de langue en**C++**

1. Sélectionnez **projet vide** , puis cliquez sur **suivant** .

1. Dans la zone de texte **nom du projet** , tapez **CodeDefects**

1. Dans la zone de texte nom de la **solution** , tapez **CppDemo**

1. Cliquez sur **Créer**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurer le projet CodeDefects comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **CodeDefects**, puis cliquez sur **Propriétés**.

1. Développez **Propriétés de configuration**, puis cliquez sur **Général**.

1. Dans la liste **général** , remplacez **type de configuration**par **bibliothèque statique (. lib)** .

1. Dans la liste **avancé** , remplacez l' **extension du fichier cible** par **. lib**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Ajouter le fichier source et d’en-tête au projet CodeDefects

1. Dans l’Explorateur de solutions, développez **CodeDefects**, cliquez avec le bouton droit sur **Fichiers d’en-tête**, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Code**, puis sur **Fichier d’en-tête (.h)** .

1. Dans le champ **Nom**, tapez **Bug.h**, puis cliquez sur **Ajouter**.

1. Copiez le code suivant et collez-le dans le fichier *bug. h* dans l’éditeur.

    ```cpp
    #pragma once

    #include <windows.h>

    // These functions are consumed by the sample
    // but are not defined. This project cannot be linked!
    bool CheckDomain(LPCTSTR);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. Dans l’Explorateur de solutions, cliquez sur **Fichiers sources**, pointez sur **Nouveau**, puis cliquez sur **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Fichier C++ (.cpp)** .

1. Dans le champ **Nom**, tapez **Bug.cpp**, puis cliquez sur **Ajouter**.

1. Copiez le code suivant et collez-le dans le fichier *bug. cpp* dans l’éditeur.

    ```cpp
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == '\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = '\0';
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

1. Cliquez sur le menu **Fichier**, puis sur **Enregistrer tout**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ajouter le projet Annotations et le configurer comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez sur **CppDemo**, pointez sur **Ajouter** et cliquez sur **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , modifiez le filtre **C++** de langue en et sélectionnez **projet vide** , puis cliquez sur **suivant**.

1. Dans la zone de texte **nom du projet** , tapez **Annotations**, puis cliquez sur **créer**.

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Annotations**, puis cliquez sur **Propriétés**.

1. Développez **Propriétés de configuration**, puis cliquez sur **Général**.

1. Dans la liste **général** , modifiez le **type de configuration**, puis cliquez sur **bibliothèque statique (. lib)** .

1. Dans la liste **avancé** , sélectionnez le texte dans la colonne en regard de **extension de fichier cible**, puis tapez **. lib**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Ajouter le fichier d’en-tête et le fichier source au projet Annotations

1. Dans l’Explorateur de solutions, développez **Annotations**, cliquez avec le bouton droit sur **Fichiers d’en-tête**, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Fichier d’en-tête (.h)** .

1. Dans la zone **Nom**, tapez **annotations.h**, puis cliquez sur **Ajouter**.

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

1. Dans l’Explorateur de solutions, cliquez sur **Fichiers sources**, pointez sur **Nouveau**, puis cliquez sur **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Code** et sur **Fichier C++ (.cpp)** .

1. Dans la zone **Nom**, tapez **annotations.cpp**, puis cliquez sur **Ajouter**.

1. Copiez le code suivant et collez-le dans le fichier *Annotations. cpp* dans l’éditeur.

    ```cpp
    #include "annotations.h"

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

1. Cliquez sur le menu **Fichier**, puis sur **Enregistrer tout**.

La solution est maintenant terminée et doit être générée sans erreurs.
