---
description: 'En savoir plus sur : conventions d’appel, paramètres et type de retour'
title: Conventions d'appel, paramètres et type de retour
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: f840ecbe3364f293e9445239984ad375eed48aac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182526"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Conventions d'appel, paramètres et type de retour

Le prototype d'une routine d'assistance est :

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Paramètres

*pidd*<br/>
**`const`** Pointeur vers un `ImgDelayDescr` qui contient les décalages de diverses données liées à l’importation, un horodatage pour les informations de liaison et un ensemble d’attributs qui fournissent des informations supplémentaires sur le contenu du descripteur. Actuellement, il n’existe qu’un seul attribut, `dlattrRva` , qui indique que les adresses du descripteur sont des adresses virtuelles relatives. Pour plus d’informations, consultez les déclarations dans *delayimp. h*.

Pour obtenir la définition de la `PCImgDelayDescr` structure, consultez [définitions de structure et de constante](structure-and-constant-definitions.md).

*ppfnIATEntry*<br/>
Pointeur vers l’emplacement dans la table d’adresses d’importation (IAT) de chargement différé qui est mis à jour avec l’adresse de la fonction importée. La routine d’assistance doit stocker la même valeur qu’elle retourne à cet emplacement.

## <a name="expected-return-values"></a>Valeurs de retour attendues

Si la fonction réussit, elle retourne l'adresse de la fonction importée.

Si la fonction échoue, elle lève une exception et retourne 0. Trois types d'exceptions peuvent être levées :

- paramètre non valide, ce qui se produit si les attributs dans `pidd` ne sont pas spécifiés correctement ;

- `LoadLibrary` a échoué sur la DLL spécifiée ;

- échec de `GetProcAddress`.

Il vous incombe de gérer ces exceptions.

## <a name="remarks"></a>Notes

La Convention d’appel de la fonction d’assistance est **`__stdcall`** . Le type de la valeur de retour n’est pas pertinent, donc FARPROC est utilisé. Cette fonction dispose d'une liaison C.

La valeur de retour de l'assistant de chargement différé doit être stockée dans l'emplacement du pointeur de fonction fourni, à moins que vous vouliez que votre routine d'assistance soit utilisée en tant que hook de notification. Dans ce cas, votre code a la responsabilité de trouver le pointeur de fonction approprié à retourner. Le code thunk que l'éditeur de liens génère prend ensuite cette valeur de retour comme cible réelle de l'importation et y accède directement.

## <a name="sample"></a>Exemple

Le code suivant illustre l'implémentation d'une fonction hook simple.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Voir aussi

[Fonctionnement de la fonction d’assistance](understanding-the-helper-function.md)
