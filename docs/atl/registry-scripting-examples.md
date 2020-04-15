---
title: Exemples de script du registre
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329330"
---
# <a name="registry-scripting-examples"></a>Exemples de script du registre

Les exemples de script dans ce sujet démontrent comment ajouter une clé au registre du système, enregistrer le serveur com registraire, et spécifier plusieurs arbres d’analyse.

## <a name="add-a-key-to-hkey_current_user"></a>Ajouter une clé à HKEY_CURRENT_USER

L’arbre d’analyse suivant illustre un script simple qui ajoute une seule clé au registre du système. En particulier, le script `MyVeryOwnKey`ajoute `HKEY_CURRENT_USER`la clé, , à . Il attribue également la valeur `HowGoesIt` de la chaîne par défaut de la nouvelle clé:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Ce script peut facilement être étendu pour définir plusieurs sous-clés comme suit:

```
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

Maintenant, le script ajoute `HasASubkey`un `MyVeryOwnKey`sous-clé, , à . Pour ce sous-clé, `PrettyCool` il ajoute à `DWORD` la fois le sous-clé (avec une valeur par défaut de 55) et la `ANameValue` valeur nommée (avec une valeur de chaîne de `WithANamedValue`).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Enregistrez le serveur COM Registrar

Le script suivant enregistre le serveur Registrar COM lui-même.

```
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

Au moment de la course, `ATL.Registrar` cet `HKEY_CLASSES_ROOT`arbre d’analyse ajoute la clé à . À cette nouvelle clé, il alors:

- Spécifie `ATL Registrar Class` comme la valeur de la chaîne par défaut de la clé.

- Ajoute `CLSID` comme un sous-clé.

- Specifie `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` `CLSID`pour . (Cette valeur est le CLSID du registraire pour une utilisation avec `CoCreateInstance`.)

Depuis `CLSID` qu’il est partagé, il ne doit pas être supprimé en mode Unregister. La déclaration, `NoRemove CLSID`, le `CLSID` fait en indiquant que doit être ouvert en mode Registre et ignoré en mode Non-enregistrement.

L’énoncé `ForceRemove` fournit une fonction d’entretien ménager en supprimant une clé et tous ses sous-clés avant de recréer la clé. Cela peut être utile si les noms des sous-clés ont changé. Dans cet exemple `ForceRemove` de script, `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` vérifie si il existe déjà. Si c’est le cas, `ForceRemove`:

- Supprime de façon `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` récursive et toutes ses sous-clés.

- Recréer `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Ajoute `ATL Registrar Class` que la valeur `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`de chaîne par défaut pour .

L’arbre d’analyse ajoute maintenant deux `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`nouveaux sous-clés à . La première `ProgID`clé, , obtient une valeur de chaîne par défaut qui est le ProgID. La deuxième `InprocServer32`clé, , obtient `%MODULE%`une valeur de chaîne par défaut, , c’est une valeur préprocesseur expliquée dans la section, [En utilisant des paramètres remplaçables (Preprocesseur du registraire)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de cet article. `InprocServer32`obtient également une `ThreadingModel`valeur nommée, , `Apartment`avec une valeur de chaîne de .

## <a name="specify-multiple-parse-trees"></a>Spécifier les arbres à parse multiples

Pour spécifier plus d’un arbre d’analyse dans un script, il suffit de placer un arbre à la fin d’un autre. Par exemple, le script suivant `MyVeryOwnKey`ajoute la clé, , `HKEY_CLASSES_ROOT` `HKEY_CURRENT_USER`aux arbres d’analyse pour les deux et :

```
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
> Dans un script de registraire, 4K est la taille maximale des jetons. (Un jeton est tout élément reconnaissable dans la syntaxe.) Dans l’exemple scriptant `HKEY_CURRENT_USER` `'MyVeryOwnKey'`précédent, `'HowGoesIt'` `HKCR`, , et sont tous des jetons.

## <a name="see-also"></a>Voir aussi

[Création de scripts registraires](../atl/creating-registrar-scripts.md)
