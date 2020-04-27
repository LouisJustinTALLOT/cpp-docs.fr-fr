---
title: Exemples de scripts du Registre
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168746"
---
# <a name="registry-scripting-examples"></a>Exemples de scripts du Registre

Les exemples de scripts de cette rubrique montrent comment ajouter une clé au registre système, inscrire le serveur de bureau d’enregistrement COM et spécifier plusieurs arborescences d’analyse.

## <a name="add-a-key-to-hkey_current_user"></a>Ajouter une clé à HKEY_CURRENT_USER

L’arborescence d’analyse suivante illustre un script simple qui ajoute une clé unique au registre système. En particulier, le script ajoute la clé, `MyVeryOwnKey`, à `HKEY_CURRENT_USER`. Elle affecte également la valeur de chaîne par défaut `HowGoesIt` de à la nouvelle clé :

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Ce script peut facilement être étendu pour définir plusieurs sous-clés, comme suit :

```rgs
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

À présent, le script ajoute une sous `HasASubkey`-clé `MyVeryOwnKey`,, à. Pour cette sous-clé, elle ajoute `PrettyCool` la sous-clé ( `DWORD` avec une valeur par défaut de `ANameValue` 55) et la valeur nommée (avec `WithANamedValue`une valeur de chaîne de).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Inscrire le serveur d’inscription COM

Le script suivant inscrit le serveur d’inscription COM.

```rgs
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

Au moment de l’exécution, cette arborescence d' `ATL.Registrar` analyse ajoute `HKEY_CLASSES_ROOT`la clé à. À cette nouvelle clé :

- Spécifie `ATL Registrar Class` comme valeur de chaîne par défaut de la clé.

- Ajoute `CLSID` en tant que sous-clé.

- `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` Spécifie `CLSID`pour. (Cette valeur est le CLSID du Bureau d’enregistrement à `CoCreateInstance`utiliser avec.)

Étant `CLSID` donné que est partagé, il ne doit pas être supprimé en mode annulation de l’inscription. Dans ce cas `NoRemove CLSID`, l’instruction indique que `CLSID` doit être ouvert en mode Register et ignoré en mode Unregister.

L' `ForceRemove` instruction fournit une fonction de maintenance en supprimant une clé et toutes ses sous-clés avant de recréer la clé. Cela peut être utile si les noms des sous-clés ont été modifiés. Dans cet exemple de script, `ForceRemove` vérifie si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` existe déjà. Si c’est le `ForceRemove`cas, procédez comme suit :

- Supprime de manière récursive `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` et toutes ses sous-clés.

- Recrée `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Ajoute `ATL Registrar Class` comme valeur de chaîne par défaut `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`pour.

L’arborescence d’analyse ajoute désormais deux nouvelles sous- `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`clés à. La première clé, `ProgID`, obtient une valeur de chaîne par défaut qui est le ProgID. La deuxième clé, `InprocServer32`, obtient une valeur de chaîne par `%MODULE%`défaut,, qui est une valeur de préprocesseur expliquée dans la section [utilisation de paramètres remplaçables (le préprocesseur du greffier)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)de cet article. `InprocServer32`obtient également une valeur nommée, `ThreadingModel`, avec une valeur de chaîne `Apartment`de.

## <a name="specify-multiple-parse-trees"></a>Spécifier plusieurs arborescences d’analyse

Pour spécifier plusieurs arborescences d’analyse dans un script, placez simplement une arborescence à la fin d’une autre. Par exemple, le script suivant ajoute la clé, `MyVeryOwnKey`, aux arborescences d’analyse pour `HKEY_CLASSES_ROOT` et `HKEY_CURRENT_USER`:

```rgs
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> Dans un script d’inscription, 4K est la taille de jeton maximale. (Un jeton est un élément reconnaissable dans la syntaxe.) Dans l’exemple de script précédent, `HKCR` `HKEY_CURRENT_USER` `'MyVeryOwnKey'`,, et `'HowGoesIt'` sont tous des jetons.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
