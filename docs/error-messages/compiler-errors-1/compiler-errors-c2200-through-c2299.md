---
title: Erreurs du compilateur C2200 à C2299 | Documents Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
dev_langs:
- C++
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 567cd6a9cbb042027b13056fe50330b31f326529
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236859"
---
# <a name="compiler-errors-c2200-through-c2299"></a>Erreurs du compilateur C2200 à C2299

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2200](compiler-error-c2200.md)|'*fonction*' : fonction déjà définie.|
|[Erreur du compilateur C2201](compiler-error-c2201.md)|'*identificateur*' : doit avoir une liaison externe pour pouvoir être importé/exporté|
|C2202 d’erreur du compilateur|'*fonction*' : une valeur de retour pas tous les chemins d’accès de contrôle|
|[Erreur du compilateur C2203](compiler-error-c2203.md)|Delete (opérateur) ne peut pas spécifier de limites pour un tableau|
|[Erreur du compilateur C2204](compiler-error-c2204.md)|'*type*' : définition de type rencontrée entre parenthèses|
|[Erreur du compilateur C2205](compiler-error-c2205.md)|'*identificateur*' : ne peut pas initialiser des variables extern avec une portée de bloc|
|[Erreur du compilateur C2206](compiler-error-c2206.md)|'*fonction*' : typedef ne peut pas être utilisé pour la définition de fonction|
|[Erreur du compilateur C2207](compiler-error-c2207.md)|'*membre*' : un membre d’un modèle de classe ne peut pas acquérir un type de fonction|
|[Erreur du compilateur C2208](compiler-error-c2208.md)|'*type*' : aucun membre défini à l’aide de ce type|
|C2209 d’erreur du compilateur|'*identificateur*' : alias ne peut pas être utilisés dans les déclarations de constructeur|
|C2210 d’erreur du compilateur|'*identificateur*' : expansions de package ne peut pas être utilisées en tant qu’arguments à des paramètres non packagés dans les modèles d’alias|
|C2211 d’erreur du compilateur|Un destructeur non virtuel dans une classe ref dérivée d’une classe ref avec un destructeur public doit également être public|
|[Erreur du compilateur C2212](compiler-error-c2212.md)|'*identificateur*' : __based non disponible pour les pointeurs vers des fonctions|
|[Erreur du compilateur C2213](compiler-error-c2213.md)|'*identificateur*' : argument non conforme pour __based|
|C2214 d’erreur du compilateur|les pointeurs basés sur 'void' nécessitent l’utilisation de : >|
|C2215 d’erreur du compilateur|'*mot clé*' ne peut pas être utilisé avec ' / arch : SSE'|
|[Erreur du compilateur C2216](compiler-error-c2216.md)|'*mot_clé1*'ne peut pas être utilisé avec'*mot Clé2*'|
|[Erreur du compilateur C2217](compiler-error-c2217.md)|'*attribute1*'requiert'*attribut2*'|
|[Erreur du compilateur C2218](compiler-error-c2218.md)|'*calltype*' ne peut pas être utilisé avec ' / arch : IA32'|
|[Erreur du compilateur C2219](compiler-error-c2219.md)|Erreur de syntaxe : le qualificateur de type doit être après ' *'|
|[Erreur du compilateur C2220](compiler-error-c2220.md)|Avertissement considéré comme une erreur : aucun '*filetype*' fichier généré|
|Erreur du compilateur C2221|Obsolète.|
|[Erreur du compilateur C2222](compiler-error-c2222.md)|type inattendu '*type*' : une classe de base ou d’un membre était attendu.|
|[Erreur du compilateur C2223](compiler-error-c2223.md)|gauche de ' ->*identificateur*' doit pointer vers struct/union|
|[Erreur du compilateur C2224](compiler-error-c2224.md)|gauche de '. *identificateur*' doit avoir un type struct/union|
|C2225 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2226](compiler-error-c2226.md)|Erreur de syntaxe : type inattendu '*type*'|
|[Erreur du compilateur C2227](compiler-error-c2227.md)|gauche de ' ->*identificateur*' doit pointer vers le type de classe/struct/union/générique|
|[Erreur du compilateur C2228](compiler-error-c2228.md)|gauche de '. *identificateur*' doit avoir classe/struct/union|
|[Erreur du compilateur C2229](compiler-error-c2229.md)|classe/struct/union '*type*' possède un tableau de taille zéro non conforme|
|C2230 d’erreur du compilateur|module introuvable '*nom*'|
|[Erreur du compilateur C2231](compiler-error-c2231.md)|'. *identificateur*' : opérande gauche pointe vers 'class/struct/union', utilisez '->'|
|[Erreur du compilateur C2232](compiler-error-c2232.md)|' ->*identificateur*' : opérande gauche avec class/struct/union ' type','.' utiliser|
|[Erreur du compilateur C2233](compiler-error-c2233.md)|'*identificateur*' : les tableaux d’objets contenant des tableaux d’indice zéro ne sont pas autorisés|
|[Erreur du compilateur C2234](compiler-error-c2234.md)|*identificateur*' : les tableaux de références ne sont pas autorisés|
|C2235 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2236](compiler-error-c2236.md)|jeton inattendu '*jeton*'. N'auriez-vous pas oublié un ';' ?|
|C2237 d’erreur du compilateur|plusieurs déclaration de module|
|[Erreur du compilateur C2238](compiler-error-c2238.md)|jetons inattendus avant '*jeton*'|
|C2239 d’erreur du compilateur|'*fonction*' : tentative de suppression d’une fonction __declspec (dllexport)|
|C2240 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2241](compiler-error-c2241.md)|'*identificateur*' : accès au membre est limitée|
|[Erreur du compilateur C2242](compiler-error-c2242.md)|nom de typedef impossible après un class/struct/union|
|[Erreur du compilateur C2243](compiler-error-c2243.md)|'*conversion_type*' : conversion de '*type1*'à'*type2*' existe mais n’est pas accessible|
|[Erreur du compilateur C2244](compiler-error-c2244.md)|'*identificateur*' : Impossible de faire correspondre la définition de fonction avec une déclaration existante|
|[Erreur du compilateur C2245](compiler-error-c2245.md)|fonction de membre inexistant '*fonction*' spécifié en tant que friend (la signature de fonction membre ne correspond à aucune surcharge)|
|[Erreur du compilateur C2246](compiler-error-c2246.md)|'*identificateur*' : les membres de données statiques non conforme dans une classe définie localement|
|[Erreur du compilateur C2247](compiler-error-c2247.md)|'*identificateur*' n’est pas accessible, car '*class1*'utilise'*spécificateur*' pour hériter de'*classe2*'|
|[Erreur du compilateur C2248](compiler-error-c2248.md)|'*identificateur*' : Impossible d’accéder à *accessibilité* *membre* déclaré dans la classe*classe*'|
|[Erreur du compilateur C2249](compiler-error-c2249.md)|'*identificateur*' : aucun chemin accessible vers *accessibilité* *membre* déclaré dans la base virtuelle '*classe*'|
|[Erreur du compilateur C2250](compiler-error-c2250.md)|'*identificateur*' : héritage ambigu de *classe*::*membre*'|
|[Erreur du compilateur C2251](compiler-error-c2251.md)|espace de noms '*espace de noms*'n’a pas de membre'*identificateur*'-voulez-vous utiliser '*membre*' ?|
|[Erreur du compilateur C2252](compiler-error-c2252.md)|une instanciation explicite d’un modèle ne peut se produire au niveau de la portée espace de noms|
|[Erreur du compilateur C2253](compiler-error-c2253.md)|'*fonction*' : spécificateur pure ou substitution abstrait uniquement autorisé sur une fonction virtuelle de spécificateur|
|[Erreur du compilateur C2254](compiler-error-c2254.md)|'*fonction*' : spécificateur pure ou substitution abstrait spécificateur non autorisé sur une fonction friend|
|[Erreur du compilateur C2255](compiler-error-c2255.md)|'*élément*' : non autorisé en dehors d’une définition de classe|
|[Erreur du compilateur C2256](compiler-error-c2256.md)|utilisation non conforme du spécificateur friend sur '*fonction*'|
|C2257 d’erreur du compilateur|'*spécificateur*' : spécificateur non autorisé dans le type de retour de fin|
|[Erreur du compilateur C2258](compiler-error-c2258.md)|syntaxe pure non conforme, doit être '= 0'|
|[Erreur du compilateur C2259](compiler-error-c2259.md)|'*classe*' : Impossible d’instancier une classe abstraite|
|C2260 d’erreur du compilateur|'*spécificateur*' : spécificateur d’assembly friend InternalsVisibleToAttribute non valide|
|[Erreur du compilateur C2261](compiler-error-c2261.md)|'*chaîne*' : référence d’assembly n’est pas valide et ne peut pas être résolue|
|[Erreur du compilateur C2262](compiler-error-c2262.md)|'*spécificateur*' : les déclarations InternalsVisibleTo ne peuvent pas avoir une version, culture ou architecture de processeur spécifiée|
|C2263 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2264](compiler-error-c2264.md)|'*fonction*' : erreur dans la déclaration ou définition de fonction ; fonction non appelée|
|Erreur du compilateur C2265|Obsolète.|
|[Erreur du compilateur C2266](compiler-error-c2266.md)|'*identificateur*' : référence à un tableau à limite non constante non conforme|
|[Erreur du compilateur C2267](compiler-error-c2267.md)|'*fonction*' : les fonctions static avec portée de bloc ne sont pas autorisées|
|[Erreur du compilateur C2268](compiler-error-c2268.md)|'*fonction*' est un programme d’assistance de bibliothèque prédéfini du compilateur. Programmes d’assistance de bibliothèque ne sont pas pris en charge avec /GL ; Compilez le fichier objet '*nom de fichier*' sans /GL.|
|C2269 d’erreur du compilateur|Impossible de créer un pointeur ou une référence à un type de fonction qualifié (nécessite un pointeur vers membre)|
|[Erreur du compilateur C2270](compiler-error-c2270.md)|'*fonction*' : modificateurs non autorisés sur les fonctions non membres|
|[Erreur du compilateur C2271](compiler-error-c2271.md)|'*fonction*' : new/delete ne peut pas comporter de modificateurs de listes formelles|
|[Erreur du compilateur C2272](compiler-error-c2272.md)|'*fonction*' : modificateurs non autorisés sur les fonctions membres static|
|[Erreur du compilateur C2273](compiler-error-c2273.md)|'*type*' : non conforme à droite de l’opérateur '->'|
|[Erreur du compilateur C2274](compiler-error-c2274.md)|'*type*' : non conforme à droite de '.' (opérateur)|
|[Erreur du compilateur C2275](compiler-error-c2275.md)|'*type*' : utilisation non conforme de ce type en tant qu’expression|
|[Erreur du compilateur C2276](compiler-error-c2276.md)|'*opérateur*' : opération non conforme sur l’expression de fonction membre liée|
|[Erreur du compilateur C2277](compiler-error-c2277.md)|'*fonction*' : ne peut pas prendre l’adresse de cette fonction membre|
|C2278 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2279](compiler-error-c2279.md)|spécification d’exception ne peut pas apparaître dans une déclaration typedef|
|[Erreur du compilateur C2280](compiler-error-c2280.md)|'*classe*::*fonction*' : tentative de référencement d’une fonction supprimée|
|C2281 d’erreur du compilateur|'*classe*::*fonction*' : une fonction peut uniquement être supprimée sur la première déclaration|
|C2282 d’erreur du compilateur|'*fonction1*'ne peut pas substituer'*fonction2*'|
|[Erreur du compilateur C2283](compiler-error-c2283.md)|'*identificateur*' : spécificateur pure ou substitution abstrait spécificateur non autorisé sur la classe/struct sans nom|
|C2284 d’erreur du compilateur|'*fonction*' : argument non conforme d’une fonction intrinsèque, paramètre *nombre*|
|[Erreur du compilateur C2285](compiler-error-c2285.md)|des pointeurs en représentation sous forme de membres a déjà été déterminée - pragma ignoré|
|[Erreur du compilateur C2286](compiler-error-c2286.md)|des pointeurs vers membres '*identificateur*' représentation est déjà définie sur *héritage* -déclaration ignorée|
|[Erreur du compilateur C2287](compiler-error-c2287.md)|'*identificateur*' : représentation d’héritage : '*inheritiance*'est moins général que le texte requis'*héritage*'|
|C2288 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2289](compiler-error-c2289.md)|même qualificateur de type utilisé plusieurs fois|
|[Erreur du compilateur C2290](compiler-error-c2290.md)|Syntaxe C++ 'asm' ignorée. Utilisez __asm.|
|C2291 d’erreur du compilateur|Un espace de noms anonyme ne peuvent pas être exportée.|
|[Erreur du compilateur C2292](compiler-error-c2292.md)|'*identificateur*' : représentation d’héritage préférentielle : *inheritance1*' déclarée mais '*et héritage 2*' requis|
|[Erreur du compilateur C2293](compiler-error-c2293.md)|'*identificateur*' : non conforme à une variable membre un spécificateur __based|
|C2294 d’erreur du compilateur|Impossible d’exporter le symbole '*identificateur*', car il possède une liaison interne|
|[Erreur du compilateur C2295](compiler-error-c2295.md)|séquence d’échappement '*caractère*' : non conforme dans une définition de macro|
|[Erreur du compilateur C2296](compiler-error-c2296.md)|'*opérateur*' : non conforme, l’opérande gauche a le type '*type*'|
|[Erreur du compilateur C2297](compiler-error-c2297.md)|'*opérateur*' : non conforme, l’opérande droit a le type '*type*'|
|[Erreur du compilateur C2298](compiler-error-c2298.md)|appel manquant pour lier le pointeur de fonction membre|
|[Erreur du compilateur C2299](compiler-error-c2299.md)|'*fonction*' : changement de comportement : une spécialisation explicite ne peut pas être un constructeur de copie ou un opérateur d’assignation de copie|
