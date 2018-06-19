---
title: C3300 des erreurs du compilateur via C3399 | Documents Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
helpviewer_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
dev_langs:
- C++
ms.assetid: 190b7d29-ffe6-4261-921d-140da1935d00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c5976e57e0a3b7f51c9df3fbdf3ebebb08dd1b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284116"
---
# <a name="compiler-errors-c3300-through-c3399"></a>C3300 des erreurs du compilateur via C3399

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|C3300 d’erreur du compilateur|'*symbole*' : format incorrect pour IDL '*valeur*'|
|C3301 d’erreur du compilateur|'*coclasse*' : coclasse ne peut pas être un '*symbole*' interface|
|C3302 d’erreur du compilateur|'*identificateur*' : identificateur possède plus de *nombre* caractères|
|[Erreur du compilateur C3303](compiler-error-c3303.md)|'*attribut*' : attribut peut uniquement être utilisé sur '*type*'|
|Erreur du compilateur C3304|Obsolète.|
|Erreur du compilateur C3305|Obsolète.|
|C3306 d’erreur du compilateur|'*modèle*' : modèle/générique de classe sans nom n’est pas autorisée.|
|C3307 d’erreur du compilateur|'*module*' : Impossible de créer de module IDL|
|C3308 d’erreur du compilateur|' *fonction*' : directe appel via la classe importée n’est pas pris en charge.|
|[Erreur du compilateur C3309](compiler-error-c3309.md)|'*macro*/*mot clé*' : nom de module ne peut pas être une macro ou un mot clé|
|C3310 d’erreur du compilateur|'*identificateur*' : conflit de nom de module|
|C3311 d’erreur du compilateur|attribut module doit être défini dans une portée globale|
|C3312 d’erreur du compilateur|ne peut être appelé «*identificateur*'fonction trouvé pour le type'*type*'|
|C3313 d’erreur du compilateur|'*identificateur*' : variable ne peut pas avoir le type '*type*'|
|C3314 d’erreur du compilateur|'*symbole*' : type de module IDL non pris en charge|
|C3315 d’erreur du compilateur|' *fonction*' : doit être une fonction membre|
|C3316 d’erreur du compilateur|'*type*' : un tableau de taille inconnue ne peut pas être utilisé dans une plage pour l’instruction|
|C3317 d’erreur du compilateur|'*identificateur*' : une fonction de surcharge ne peut pas être utilisée que l’expression dans une plage pour l’instruction|
|C3318 d’erreur du compilateur|'*type*' : un tableau ne peut pas avoir un type d’élément qui contient « auto »|
|C3319 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C3320](compiler-error-c3320.md)|'*type*' : type ne peut pas avoir le même nom que la propriété 'name' du module|
|C3321 d’erreur du compilateur|une liste d’initialiseurs est inattendue dans ce contexte|
|[Erreur du compilateur C3322](compiler-error-c3322.md)|'*propriété*' : n’est pas une propriété valide pour l’attribut '*attribut*'|
|C3323 d’erreur du compilateur|'alignas' et '__declspec (Align)' ne sont pas autorisés sur les déclarations de fonction|
|C3324 d’erreur du compilateur|'*propriété*' : propriété apparaît plusieurs fois dans l’attribut '*attribut*'|
|C3325 d’erreur du compilateur|'*attribut*' : trop d’arguments pour l’attribut|
|C3326 d’erreur du compilateur|'*valeur*' : n’est pas une valeur valide pour la propriété '*propriété*'de l’attribut'*attribut*'|
|C3327 d’erreur du compilateur|'*propriété*' : doit spécifier la valeur de propriété d’attribut '*attribut*'|
|C3328 d’erreur du compilateur|'*attribut*' : attribut n’a pas assez d’arguments|
|C3329 d’erreur du compilateur|Erreur de syntaxe : attendu '*token1*'not'*token2*'|
|C3330 d’erreur du compilateur|' *fonction*' : une fonction ne peut pas retourner un tableau '*type*'|
|C3331 d’erreur du compilateur|'*identificateur*' : attributs sur les paramètres sont autorisés uniquement sur les coclasses et les interfaces COM|
|C3332 d’erreur du compilateur|'*propriété*' : les propriétés incohérentes, grammaire '*propriété*' est à la fois requis et a une valeur par défaut|
|[Erreur du compilateur C3333](compiler-error-c3333.md)|'*bibliothèque*' : #import de bibliothèque de types endommagée Impossible|
|[Erreur du compilateur C3334](compiler-error-c3334.md)|#import de bibliothèque de types endommagée impossible|
|C3335 d’erreur du compilateur|'*identificateur*' : il peut y avoir au plus une interface par défaut pour d’une coclasse*classe*'|
|C3336 d’erreur du compilateur|Cette opération doit être effectuée au niveau de portée de classe|
|C3337 d’erreur du compilateur|'*identificateur*' : defaultvtable doit être une source d’événements pour d’une coclasse*classe*'|
|C3338 d’erreur du compilateur|'*identificateur*' : il peut y avoir au plus une interface par défaut qui est également une source d’événements pour d’une coclasse*classe*'|
|C3339 d’erreur du compilateur|paramètre de modèle requiert 'class' ou 'typename' après la liste de paramètres|
|[Erreur du compilateur C3340](compiler-error-c3340.md)|'*identificateur*' : interface ne peut pas être à la fois 'restricted' et 'default' dans la coclasse*classe*'|
|C3341 d’erreur du compilateur|'*interface*' : une interface defaultvtable doit être 'dual' ou 'custom'|
|[Erreur du compilateur C3342](compiler-error-c3342.md)|'*identificateur*' : attribut ambigu|
|C3343 d’erreur du compilateur|'*classe*::*nom*' : identificateur d’attribut a trop de caractères|
|C3344 d’erreur du compilateur|Vous ne pouvez pas définir une spécialisation explicite ni une spécialisation partielle de '*symbole*'|
|[Erreur du compilateur C3345](compiler-error-c3345.md)|'*nom*' : identificateur non valide pour le nom du module|
|C3346 d’erreur du compilateur|déclaration exportée en portée espace de noms non|
|[Erreur du compilateur C3347](compiler-error-c3347.md)|'*argument*' : argument requis n'est pas spécifié dans l’attribut *asttribute*|
|C3348 d’erreur du compilateur|les modèles exportés ne font pas partie des normes C++ actuelles|
|C3349 d’erreur du compilateur|'*classe*::*membre*' : attribut multicast a déjà été implémenté par le fournisseur *fournisseur*|
|[Erreur du compilateur C3350](compiler-error-c3350.md)|' *fonction*' : un constructeur délégué attend *nombre* argument (s)|
|[Erreur du compilateur C3351](compiler-error-c3351.md)|' *fonction*' : Si vous passez une instance d’objet NULL à un constructeur délégué vous devez également passer l’adresse d’une fonction membre statique|
|[Erreur du compilateur C3352](compiler-error-c3352.md)|'*fonction*' : la fonction spécifiée ne correspond pas au type délégué '*type*'|
|[Erreur du compilateur C3353](compiler-error-c3353.md)|'*identificateur*' : un délégué ne peut être créé qu’à partir d’une fonction globale ou une fonction membre d’un type managé/WinRT|
|[Erreur du compilateur C3354](compiler-error-c3354.md)|'*identificateur*' : la fonction utilisée pour créer un délégué ne peut pas avoir de type de retour '*type*'|
|C3355 d’erreur du compilateur|'*classe*::*membre*' : attribut multicast écoute le fournisseur '*Fournisseur1*», mais est implémenté par le fournisseur '*FOURNISSEUR2*'|
|[Erreur du compilateur C3356](compiler-error-c3356.md)|'*identificateur*' : Impossible d’appeler un attribut multicast avec un nom qualifié complet|
|C3357 d’erreur du compilateur|'*attribut*' : attribut est ambigu, il doit utiliser de nom qualifié complet|
|[Erreur du compilateur C3358](compiler-error-c3358.md)|'*symbole*' : symbole non trouvé|
|C3359 d’erreur du compilateur|'*spécialisation*' : Impossible de spécialiser le modèle|
|[Erreur du compilateur C3360](compiler-error-c3360.md)|'*chaîne*' : Impossible de créer *nom*|
|C3361 d’erreur du compilateur|Il n’existe aucun contexte dans lequel *action*|
|C3362 d’erreur du compilateur|'*classe*::*membre*' : attribut multicast n’a pas été implémentée.|
|[Erreur du compilateur C3363](compiler-error-c3363.md)|'*identificateur*' : 'typeid' peut uniquement être appliqué à un type|
|[Erreur du compilateur C3364](compiler-error-c3364.md)|' *fonction*' : argument non valide pour le constructeur délégué ; la cible du délégué doit être un pointeur vers une fonction membre|
|[Erreur du compilateur C3365](compiler-error-c3365.md)|opérateur '*opérateur*' : opérandes différents de type '*type*'et'*type*'|
|[Erreur du compilateur C3366](compiler-error-c3366.md)|'*membre*' : données membres static des types gérés/WinRT doivent être définies dans la définition de classe|
|[Erreur du compilateur C3367](compiler-error-c3367.md)|' *fonction*' : ne peut pas utiliser une fonction static pour créer un délégué indépendant|
|[Erreur du compilateur C3368](compiler-error-c3368.md)|'*déclarateur*' : convention d’appel non valide pour IDL|
|[Erreur du compilateur C3369](compiler-error-c3369.md)|'*module*' : module idl_module déjà défini|
|[Erreur du compilateur C3370](compiler-error-c3370.md)|'*module*' : module idl_module non encore défini|
|[Erreur du compilateur C3371](compiler-error-c3371.md)|'idl_module' : seule la propriété 'name' est autorisée ici|
|[Erreur du compilateur C3372](compiler-error-c3372.md)|doit spécifier au moins 1 interface pour l’attribut '*attribut*' d’une coclasse|
|[Erreur du compilateur C3373](compiler-error-c3373.md)|attribut '*attribut*' n’accepte aucun argument sauf sur une coclasse|
|[Erreur du compilateur C3374](compiler-error-c3374.md)|Impossible de prendre l’adresse de ' *fonction*' à moins de créer l’instance de délégué|
|[Erreur du compilateur C3375](compiler-error-c3375.md)|'*fonction*' : fonction déléguée ambiguë|
|Erreur C3376 erreur de compilateur|'*modèle*' : seuls les modèles de membre de données statiques sont autorisées.|
|C3377 d’erreur du compilateur|'decltype (auto)' n’est pas autorisée dans une expression new|
|C3378 d’erreur du compilateur|une déclaration peut être exportée uniquement à partir d’une unité d’interface de module|
|[Erreur du compilateur C3379](compiler-error-c3379.md)|'*classe*' : une classe imbriquée ne peut pas avoir de spécificateur d’accès d’assembly dans le cadre de sa déclaration|
|[Erreur du compilateur C3380](compiler-error-c3380.md)|'*spécificateur*' : assembly non valide spécificateur d’accès - seuls 'public' ou 'private' est autorisé.|
|[Erreur du compilateur C3381](compiler-error-c3381.md)|'*spécificateur*' : les spécificateurs d’accès assembly ne sont disponibles dans le code compilé avec l’option /clr|
|[Erreur du compilateur C3382](compiler-error-c3382.md)|'sizeof' n'est pas pris en charge avec /clr:safe|
|[Erreur du compilateur C3383](compiler-error-c3383.md)|'operator new' n'est pas pris en charge avec /clr:safe|
|[Erreur du compilateur C3384](compiler-error-c3384.md)|'*type*' : la contrainte de valeur et la contrainte ref s’excluent mutuellement|
|[Erreur du compilateur C3385](compiler-error-c3385.md)|' *fonction*' : une fonction qui a un attribut personnalisé DllImport ne peut pas retourner une instance d’une classe|
|[Erreur du compilateur C3386](compiler-error-c3386.md)|'*type*' : __declspec(dllexport)/__declspec(dllimport) ne peut pas être appliqué à un type managé/WinRT|
|[Erreur du compilateur C3387](compiler-error-c3387.md)|'*membre*' : __declspec(dllexport)/__declspec(dllimport) ne peut pas être appliqué à un membre d’un type managé/WinRT|
|[Erreur du compilateur C3388](compiler-error-c3388.md)|'*jeton*' : non autorisé comme contrainte, en supposant que '*valeur*» pour poursuivre l’analyse|
|[Erreur du compilateur C3389](compiler-error-c3389.md)|__declspec (*spécificateur*) ne peut pas être utilisé avec/clr : pure ou/CLR : safe|
|[Erreur du compilateur C3390](compiler-error-c3390.md)|'*type*' : argument de type non valide pour le paramètre générique '*paramètre*'du générique'*type_générique*', doit être un type référence|
|[Erreur du compilateur C3391](compiler-error-c3391.md)|'*type*' : argument de type non valide pour le paramètre générique '*paramètre*'du générique'*type_générique*', doit être un type valeur non nullable|
|[Erreur du compilateur C3392](compiler-error-c3392.md)|'*type*' : argument de type non valide pour le paramètre générique '*paramètre*'du générique'*type_générique*', doit avoir un constructeur sans paramètre public|
|[Erreur du compilateur C3393](compiler-error-c3393.md)|Erreur de syntaxe dans la clause de contrainte : '*identificateur*' n’est pas un type|
|[Erreur du compilateur C3394](compiler-error-c3394.md)|Erreur de syntaxe dans la clause de contrainte : trouvé '*symbole*' type attendu|
|[Erreur du compilateur C3395](compiler-error-c3395.md)|' *fonction*' : __declspec (dllexport) ne peut pas être appliqué à une fonction avec la convention d’appel __clrcall|
|[Erreur du compilateur C3396](compiler-error-c3396.md)|'*classe*. *membre*' : attribut personnalisé introuvable dans '*espace de noms*'|
|[Erreur du compilateur C3397](compiler-error-c3397.md)|L'initialisation d'agrégats n'est pas autorisée dans les arguments par défaut|
|[Erreur du compilateur C3398](compiler-error-c3398.md)|'*opérateur*' : Impossible de convertir '*type*'à'*type*'. L'expression source doit être un symbole de fonction|
|[Erreur du compilateur C3399](compiler-error-c3399.md)|'*type*' : ne peut pas fournir des arguments lors de la création d’une instance d’un paramètre générique|
