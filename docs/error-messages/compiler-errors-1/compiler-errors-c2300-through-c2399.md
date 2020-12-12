---
description: 'En savoir plus sur : Erreurs du compilateur C2300 à C2399'
title: Erreurs du compilateur C2300 à C2399
ms.date: 04/21/2019
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 95763db7f8be0c0918d2f15f515f327325c386dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318947"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Erreurs du compilateur C2300 à C2399

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2300](compiler-error-c2300.md)|'*classe*' : la classe n’a pas de destructeur appelé' ~*Class*'|
|[Erreur du compilateur C2301](compiler-error-c2301.md)|la partie gauche de'->~*identificateur*'doit pointer vers un class/struct/union|
|[Erreur du compilateur C2302](compiler-error-c2302.md)|la partie gauche de'. ~*identifier*'doit avoir un type class/struct/union|
|Erreur du compilateur C2303|Impossible d’utiliser la gestion structurée des exceptions dans une Coroutine|
|Erreur du compilateur C2304|'*Keyword*'ne peut pas être utilisé dans un bloc catch|
|Erreur du compilateur C2305|'*fichier*'ne contient pas d’informations de débogage pour ce module|
|Erreur du compilateur C2306|'*fichier*'ne contient pas les dernières informations de débogage pour ce module|
|[Erreur du compilateur C2307](compiler-error-c2307.md)|la *directive* pragma doit être déplacée en dehors de la fonction si la compilation incrémentielle est activée|
|[Erreur du compilateur C2308](compiler-error-c2308.md)|concaténation de chaînes incompatibles|
|[Erreur du compilateur C2309](compiler-error-c2309.md)|Déclaration d’exception entre parenthèses attendue par le gestionnaire catch|
|[Erreur du compilateur C2310](compiler-error-c2310.md)|les gestionnaires catch doivent spécifier un type|
|[Erreur du compilateur C2311](compiler-error-c2311.md)|'*type*' : intercepté par'... ' *numéro* de ligne|
|[Erreur du compilateur C2312](compiler-error-c2312.md)|'*type1*' : intercepté par'*type2*'à la ligne' *numéro* '|
|[Erreur du compilateur C2313](compiler-error-c2313.md)|'*type1*' : intercepté par la référence ('*type2*') à la *ligne*|
|Erreur du compilateur C2314|le mot clé'*keyword1*'est déconseillé : utilisez'*keyword2*'à la place|
|[Erreur du compilateur C2315](compiler-error-c2315.md)|'*type1*' : la référence est interceptée par'*type2*'à la ligne' *numéro* '|
|[Erreur du compilateur C2316](compiler-error-c2316.md)|'*type*' : ne peut pas être intercepté en tant que destructeur et/ou le constructeur de copie est inaccessible ou supprimé|
|[Erreur du compilateur C2317](compiler-error-c2317.md)|le bloc’Try’commençant à la ligne'*Number*'n’a pas de gestionnaires catch|
|[Erreur du compilateur C2318](compiler-error-c2318.md)|aucun bloc try associé à ce gestionnaire catch|
|[Erreur du compilateur C2319](compiler-error-c2319.md)|'try/catch' doit être suivi(e) d’une instruction composée. Accolade '{' manquante|
|[Erreur du compilateur C2320](compiler-error-c2320.md)|' : 'attendu pour suivre le spécificateur d’accès'*spécificateur*'|
|Erreur du compilateur C2321|'*identifier*'est un mot clé et ne peut pas être utilisé dans ce contexte|
|[Erreur du compilateur C2322](compiler-error-c2322.md)|'*identificateur*' : adresse de DllImport'*identificateur*'non statique|
|Erreur du compilateur C2323|'*identificateur*' : les fonctions opérateur non membre New ou DELETE ne peuvent pas être déclarées static ou dans un espace de noms autre que l’espace de noms global|
|[Erreur du compilateur C2324](compiler-error-c2324.md)|'*identificateur*' : inattendu à droite de' :: ~ '|
|[Erreur du compilateur C2325](compiler-error-c2325.md)|'*type1*' : type inattendu à droite de'->~ ' : '*type2*'attendu|
|[Erreur du compilateur C2326](compiler-error-c2326.md)|'*declarator*' : la fonction ne peut pas accéder à'*identifier*'|
|[Erreur du compilateur C2327](compiler-error-c2327.md)|'*identifier*' : n’est pas un nom de type, static ou Enumerator|
|Erreur du compilateur C2328|'*Keyword*' : le mot clé n’est pas encore pris en charge|
|Erreur du compilateur C2329|'*identificateur*' : __ptr64 pas disponible pour les pointeurs vers des fonctions|
|Erreur du compilateur C2330|'implementation_key () 'n’est valide que dans une région délimitée par #pragma start_map_region/stop_map_region|
|Erreur du compilateur C2331|l’accès à'*identifier*'est désormais défini comme'*accessibility1*', auparavant défini comme'*accessibility2*'|
|[Erreur du compilateur C2332](compiler-error-c2332.md)|'*typedef*' : nom de balise manquant|
|[Erreur du compilateur C2333](compiler-error-c2333.md)|'*fonction*' : erreur dans la déclaration de fonction ; corps de la fonction ignoré|
|[Erreur du compilateur C2334](compiler-error-c2334.md)|jetons inattendus avant'*Token*'; corps de la fonction apparent ignoré|
|Erreur du compilateur C2335|'*identificateur*' : un type ne peut pas être introduit dans une liste de paramètres de fonction|
|Erreur du compilateur C2336|'*type*' : type non conforme|
|[Erreur du compilateur C2337](compiler-error-c2337.md)|'*attribute*' : attribut introuvable|
|[Erreur du compilateur C2338](compiler-error-c2338.md)|*(message d’erreur du fournisseur externe)*|
|Erreur du compilateur C2339|'*identificateur*' : type non conforme dans un IDL incorporé|
|Erreur du compilateur C2340|'*identificateur*' : 'static’peut uniquement être utilisé dans une définition de classe|
|[Erreur du compilateur C2341](compiler-error-c2341.md)|'*section*' : le segment doit être défini à l’aide de #pragma data_seg, code_seg ou section avant d’être utilisé|
|Erreur du compilateur C2342|erreur de syntaxe : conflit entre qualificateurs de type|
|Erreur du compilateur C2343|'*section*' : attributs de section en conflit|
|[Erreur du compilateur C2344](compiler-error-c2344.md)|align (*Number*) : l’alignement doit être une puissance de deux|
|[Erreur du compilateur C2345](compiler-error-c2345.md)|align (*Number*) : valeur d’alignement non conforme|
|[Erreur du compilateur C2346](compiler-error-c2346.md)|'*fonction*'ne peut pas être compilé comme code natif : '*explication*'|
|Erreur du compilateur C2347|Obsolète.|
|[Erreur du compilateur C2348](compiler-error-c2348.md)|'*type*' : n’est pas un agrégat de style C, ne peut pas être exporté dans un IDL incorporé|
|[Erreur du compilateur C2349](compiler-error-c2349.md)|'*Function*'ne peut pas être compilé comme managé : '*explication*'; utiliser #pragma non géré|
|[Erreur du compilateur C2350](compiler-error-c2350.md)|'*identifier*'n’est pas un membre static|
|[Erreur du compilateur C2351](compiler-error-c2351.md)|syntaxe obsolète d’initialisation d’un constructeur C++|
|[Erreur du compilateur C2352](compiler-error-c2352.md)|'*identificateur*' : appel non conforme d’une fonction membre non statique|
|[Erreur du compilateur C2353](compiler-error-c2353.md)|spécification d’exception non autorisée|
|Erreur du compilateur C2354|Obsolète.|
|[Erreur du compilateur C2355](compiler-error-c2355.md)|'This' : ne peut être référencé qu’à l’intérieur de fonctions membres non static ou d’initialiseurs de données membres non statiques|
|[Erreur du compilateur C2356](compiler-error-c2356.md)|le segment d’initialisation ne doit pas changer pendant l’unité de traduction|
|[Erreur du compilateur C2357](compiler-error-c2357.md)|'*identificateur*' : doit être une fonction de type'*type*'|
|Erreur du compilateur C2358|'*identificateur*' : une propriété statique ne peut pas être définie en dehors d’une définition de classe|
|Erreur du compilateur C2359|Obsolète.|
|[Erreur du compilateur C2360](compiler-error-c2360.md)|l’initialisation de'*identifier*'est ignorée par l’étiquette’case'|
|[Erreur du compilateur C2361](compiler-error-c2361.md)|l’initialisation de'*identifier*'est ignorée par l’étiquette’default'|
|[Erreur du compilateur C2362](compiler-error-c2362.md)|l’initialisation de'*identifier*'est ignorée par’GoTo *label*'|
|Erreur du compilateur C2363|la fonction de limite numérique intrinsèque du compilateur nécessite un argument de littéral de chaîne|
|[Erreur du compilateur C2364](compiler-error-c2364.md)|'*type*' : type non conforme pour un attribut personnalisé|
|[Erreur du compilateur C2365](compiler-error-c2365.md)|'*membre1*' : redéfinition ; la définition précédente était'*membre2*'|
|Erreur du compilateur C2366|'*identificateur*' : redéfinition ; différents spécificateurs de implementation_key|
|Erreur du compilateur C2367|Obsolète.|
|[Erreur du compilateur C2368](compiler-error-c2368.md)|'*identificateur*' : redéfinition ; spécificateurs d’allocation différents|
|[Erreur du compilateur C2369](compiler-error-c2369.md)|'*identificateur*' : redéfinition ; indices différents|
|[Erreur du compilateur C2370](compiler-error-c2370.md)|'*identificateur*' : redéfinition ; classe de stockage différente|
|[Erreur du compilateur C2371](compiler-error-c2371.md)|'*identificateur*' : redéfinition ; types de base différents|
|[Erreur du compilateur C2372](compiler-error-c2372.md)|'*identificateur*' : redéfinition ; différents types d’indirection|
|[Erreur du compilateur C2373](compiler-error-c2373.md)|'*identificateur*' : redéfinition ; modificateurs de type différents|
|[Erreur du compilateur C2374](compiler-error-c2374.md)|'*identificateur*' : redéfinition ; initialisation multiple|
|[Erreur du compilateur C2375](compiler-error-c2375.md)|'*identificateur*' : redéfinition ; liaison différente|
|[Erreur du compilateur C2376](compiler-error-c2376.md)|'*identificateur*' : redéfinition ; allocation basée sur différentes|
|[Erreur du compilateur C2377](compiler-error-c2377.md)|'*identificateur*' : redéfinition ; typedef ne peut pas être surchargé avec un autre symbole|
|[Erreur du compilateur C2378](compiler-error-c2378.md)|'*identificateur*' : redéfinition ; le symbole ne peut pas être surchargé avec un typedef|
|[Erreur du compilateur C2379](compiler-error-c2379.md)|le *nombre* de paramètres formels a un type différent lors de sa promotion|
|[Erreur du compilateur C2380](compiler-error-c2380.md)|type (s) précédant'*identifier*' (constructeur avec type de retour ou redéfinition non conforme de Class-Name actuel ?)|
|[Erreur du compilateur C2381](compiler-error-c2381.md)|'*identificateur*' : redéfinition ; ' __declspec (noreturn) 'ou' [[noreturn]] 'est différent|
|[Erreur du compilateur C2382](compiler-error-c2382.md)|'*identificateur*' : redéfinition ; spécifications d’exceptions différentes|
|[Erreur du compilateur C2383](compiler-error-c2383.md)|'*identificateur*' : les arguments par défaut ne sont pas autorisés sur ce symbole|
|[Erreur du compilateur C2384](compiler-error-c2384.md)|'*membre*' : impossible d’appliquer thread_local ou __declspec (thread) à un membre d’une classe managée/WinRT|
|[Erreur du compilateur C2385](compiler-error-c2385.md)|accès ambigu de'*member*'|
|[Erreur du compilateur C2386](compiler-error-c2386.md)|'*identificateur*' : un symbole portant ce nom existe déjà dans la portée actuelle|
|[Erreur du compilateur C2387](compiler-error-c2387.md)|'*identificateur*' : classe de base ambiguë|
|[Erreur du compilateur C2388](compiler-error-c2388.md)|'*identificateur*' : un symbole ne peut pas être déclaré avec __declspec (AppDomain) et __declspec (processus)|
|[Erreur du compilateur C2389](compiler-error-c2389.md)|'*opérateur*' : opérande’nullptr’non conforme|
|[Erreur du compilateur C2390](compiler-error-c2390.md)|'*identificateur*' : classe de stockage incorrecte'*specifier*'|
|[Erreur du compilateur C2391](compiler-error-c2391.md)|'*identifier*' : 'Friend’ne peut pas être utilisé lors de la définition de type|
|[Erreur du compilateur C2392](compiler-error-c2392.md)|'*membre1*' : les types de retour covariants ne sont pas pris en charge dans les types managés/WinRT ; sinon, '*membre2*'est substitué|
|[Erreur du compilateur C2393](compiler-error-c2393.md)|'*symbol*' : un symbole par AppDomain ne peut pas être alloué dans le segment'*segment*'|
|[Erreur du compilateur C2394](compiler-error-c2394.md)|'*type*:: Operator *opérateur*' : opérateur CLR/WinRT non valide. Au moins un paramètre doit être de l’un des types suivants : 't ^ ', 't ^% ', 't ^& ', où T = '*type*'|
|[Erreur du compilateur C2395](compiler-error-c2395.md)|'*type*:: Operator *opérateur*' : opérateur CLR/WinRT non valide. Au moins un paramètre doit être de l’un des types suivants : 't', 't% ', 't& ', 't ^ ', 't ^% ', 't ^& ', où T = '*type*'|
|[Erreur du compilateur C2396](compiler-error-c2396.md)|'*type1*:: Operator *type2*' : fonction de conversion définie par l’utilisateur CLR/WinRT non valide. Convert from ou Convert to : 't ^ ', 't ^% ', 't ^& ', où T = '*type1*'|
|[Erreur du compilateur C2397](compiler-error-c2397.md)|la conversion de'*type1*'en'*type2*'requiert une conversion restrictive|
|Erreur du compilateur C2398|Élément'*Number*' : la conversion de'*type1*'en'*type2*'requiert une conversion restrictive|
|Erreur du compilateur C2399|Obsolète.|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
