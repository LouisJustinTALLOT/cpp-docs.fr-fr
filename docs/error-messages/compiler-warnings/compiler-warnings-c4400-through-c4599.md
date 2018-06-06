---
title: C4400 des avertissements du compilateur via C4599 | Documents Microsoft
ms.date: 05/30/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
dev_langs:
- C++
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71dbf1817c43c5511f8ee711abf3ff3566f314c9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704683"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>C4400 des avertissements du compilateur via C4599

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Warning|Message|
|-------------|-------------|
|[Avertissement du compilateur (niveau 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*nom de la macro*' : chaîne valide non vide attendue|
|[Avertissement du compilateur (niveau 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*type*' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.|
|[Avertissement du compilateur (niveau 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*champ de bits*' : membre est un champ de bits|
|[Avertissement du compilateur (niveau 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|doit utiliser l’opérateur PTR|
|[Avertissement du compilateur (niveau 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|opérateur PTR non conforme|
|[Avertissement du compilateur (niveau 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|période sur directive ignoré|
|[Avertissement du compilateur (niveau 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identificateur*' : identificateur est un mot réservé|
|[Avertissement du compilateur (niveau 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|opérande sur directive ignoré|
|[Avertissement du compilateur (niveau 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|cast entre différentes représentations du pointeur en membre, le compilateur peut générer du code incorrect|
|[Avertissement du compilateur (niveau 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anonyme ' struct&#124;union' n’a déclaré aucune donnée membre|
|[Avertissement du compilateur (niveau 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|taille d’instruction non conforme|
|[Avertissement du compilateur (niveau 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|taille non conforme d’opérande|
|[Avertissement du compilateur (niveau 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identificateur*' : symbole se résout en registre de déplacement|
|[Avertissement du compilateur (niveau 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*fonction*' : signature de fonction contient le type '*type*' ; Objets C++ sont unsafe à passer entre le code pure et mixte ou natif.|
|Avertissement C4413 du compilateur|'classname::member' : membre de référence est initialisé en temporaire qui ne persiste pas après l’arrêt du constructeur|
|[Avertissement du compilateur (niveau 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*fonction*' : saut de type short vers la fonction converti en near|
|Avertissement du compilateur (niveau 1) C4415|en double __declspec (code_seg ('*nom*'))|
|Avertissement du compilateur (niveau 1) C4416|__declspec(code_seg(...)) contient une chaîne vide : ignoré|
|Avertissement du compilateur (niveau 1) C4417|une instanciation explicite du modèle ne peut pas avoir __declspec(code_seg(...)) : ignoré|
|Avertissement du compilateur (niveau 1) C4418|__declspec(code_seg(...)) ignoré sur un enum|
|Avertissement du compilateur (niveau 3) C4419|'*symbole*'n’a aucun effet lorsqu’il est appliqué à une classe ref privée'*classe*'.|
|[Avertissement du compilateur (niveau 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*' : opérateur non disponible, à l’aide de '*opérateur*' à la place ; le contrôle à l’exécution peut être compromis|
|Avertissement du compilateur (niveau 3) C4421|'*paramètre*' : un paramètre de référence sur une fonction peut être repris est potentiellement dangereux|
|Avertissement du compilateur (niveau 3) C4423|'std::bad_alloc' : sera intercepté par la classe ('*type*») sur la ligne *nombre*|
|Avertissement du compilateur (niveau 3) C4424|interception de '*type1*'précédé de'*type2*' sur la ligne *nombre*; imprévisible comportement peut provoquer des cas de levée 'd’exception std::bad_alloc'|
|Avertissement du compilateur (niveau 1) C4425|Une annotation SAL ne peut pas être appliquée à '...'|
|Avertissement du compilateur (niveau 1) C4426|indicateurs d’optimisation modifiés après l’en-tête, peut être dû à #pragma optimize()|
|Avertissement du compilateur (niveau 1) C4427|'*opérateur*' : dépassement en division constante, un comportement non défini|
|[Avertissement du compilateur (niveau 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|possible incomplet ou incorrectement formé universel-nom de caractère|
|[Avertissement (erreur) du compilateur C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut|
|[Avertissement du compilateur (niveau 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut|
|[Avertissement du compilateur (niveau 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|un constructeur static doit avoir un accès privé ; la modification d’un accès privé|
|[Avertissement du compilateur (niveau 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*' : disposition des objets sous/vd2 sera modifiée en raison de la base virtuelle '*base_class*'|
|[Avertissement du compilateur (niveau 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dynamique\_effectué à partir de la base virtuelle '*base_class*'à'*derived_class*' dans le constructeur ou un destructeur risque d’échouer avec un objet partiellement construit|
|[Avertissement du compilateur (niveau 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dynamique\_effectué à partir de la base virtuelle '*base_class*'à'*derived_class*' risque d’échouer dans certains contextes|
|Avertissement C4438 du compilateur|'*fonction*' : ne peut pas être appelée en toute sécurité / await : clrcompat mode. Si '*fonction*' appelle le CLR, cela peut entraîner une altération de la tête de CLR|
|[Avertissement (erreur) du compilateur C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*fonction*' : définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall|
|[Avertissement du compilateur (niveau 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|redéfinition de la convention d’appel '*convention_appel1*'à'*calling_convenction2*' ignoré|
|[Avertissement du compilateur (niveau 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|convention d’appel de '*convention_appel1*' ignorée ; '*convention_appel2*' utilisé à la place|
|Avertissement du compilateur (niveau 1) C4442|un argument __annotation, incorporé marque de fin null.  Valeur sera tronquée.|
|Avertissement du compilateur (niveau 1) C4443|paramètre pragma attendu doit être '0', '1' ou '2'|
|Avertissement du compilateur (niveau 3) C4444|'*identificateur*' : '__unaligned' de niveau supérieur n’est pas implémenté dans ce contexte|
|[Avertissement du compilateur (niveau 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*fonction*' : dans un ' WinRT&#124;gérés ' type une méthode virtuelle ne peut pas être privée|
|Avertissement du compilateur (niveau 1) C4446|'*type*' : Impossible de mapper le membre '*nom1*' dans ce type, en raison de conflits avec le nom de type. La méthode a été renommée en «*name2*'|
|Avertissement du compilateur (niveau 1) C4447|signature 'main' trouvée sans modèle de thread. Envisagez d’utiliser ' int main (Platform::Array\<Platform::String ^ > ^ args)'.|
|Avertissement C4448 du compilateur|'*type*1' n’a pas d’interface par défaut spécifiée dans les métadonnées. Prélèvement : '*type2*», qui peut échouer au moment de l’exécution.|
|Avertissement C4449 du compilateur|'*type*' un type unsealed doit être marqué comme '[WebHostHidden]'|
|Avertissement C4450 du compilateur|'*type1*'doit être marqué comme '[WebHostHidden]', car il dérive de'*type2*'|
|Avertissement du compilateur (niveau 4) C4451|'classname1::member' : l’utilisation de la classe de référence 'classname2::member' à l’intérieur de ce contexte peut entraîner un marshaling non valide d’objet entre plusieurs contextes|
|Avertissement du compilateur (niveau 1) C4452|'*identificateur*' : type public ne peut pas être dans une portée globale. Il doit être dans un espace de noms qui est un enfant du nom du fichier .winmd de sortie.|
|Avertissement du compilateur (niveau 1) C4453|'*type*' : un type de '[WebHostHidden]' ne doit pas être utilisé sur la surface publiée d’un type public qui n’est pas '[WebHostHidden]'|
|Avertissement du compilateur (niveau 1) C4454|'*fonction*' est surchargé par plus que le nombre de paramètres d’entrée sans avoir [defaultoverload pour] spécifié. Prélèvement '*déclaration*' en tant que la surcharge par défaut|
|Avertissement du compilateur (niveau 1) C4455|' opérateur *opérateur*' : les identificateurs de suffixe littéral qui ne commencent pas par un trait de soulignement sont réservés.|
|[Avertissement du compilateur (niveau 4) C4456](compiler-warning-level-4-c4456.md)|déclaration de '*identificateur*' masque la déclaration locale précédente|
|[Avertissement du compilateur (niveau 4) C4457](compiler-warning-level-4-c4457.md)|déclaration de '*identificateur*' paramètre de fonction de masque|
|[Avertissement du compilateur (niveau 4) C4458](compiler-warning-level-4-c4458.md)|déclaration de '*identificateur*' masque le membre de classe|
|[Avertissement du compilateur (niveau 4) C4459](compiler-warning-level-4-c4459.md)|déclaration de '*identificateur*' masque la déclaration globale|
|[Avertissement du compilateur (niveau 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT&#124;gérés ' opérateur '*opérateur*», a paramètre passé par référence. ' WinRT&#124;gérés ' opérateur '*opérateur*'a une sémantique différente de l’opérateur C++'*cpp_operator*», souhaitiez-vous passage par valeur ?|
|[Avertissement du compilateur (niveau 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*' : cette classe a un finaliseur ' ! *finaliseur*' mais pas de destructeur ' ~*dtor*'|
|[Avertissement (niveau 1, erreur) du compilateur C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*type*' : ne peut pas déterminer le GUID du type. Le programme risque d'échouer au moment de l'exécution.|
|[Avertissement du compilateur (niveau 4) C4463](compiler-warning-level-4-c4463.md)|dépassement de capacité ; affectation '*valeur*'pour le champ de bits qui peut contenir uniquement des valeurs à partir de'*min_value*'à'*max_value*'|
|[Avertissement du compilateur (niveau 4) C4464](../../error-messages/compiler-warnings/c4464.md)|chemin include relatif contient '..'|
|[Avertissement du compilateur (niveau 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de contrôle à virgule flottante ignorés sous /clr|
|[Avertissement du compilateur (niveau 4) C4471](compiler-warning-level-4-c4471.md)|'*énumération*' : une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int pris par défaut)|
|Avertissement du compilateur (niveau 1) C4472|'*identificateur*' est un enum natif : ajoutez un spécificateur d’accès (private/public) pour déclarer un ' WinRT&#124;gérés ' enum|
|[Avertissement du compilateur (niveau 1) C4473](c4473.md)|'*fonction*' : pas assez d’arguments passés pour la chaîne de format|
|Avertissement du compilateur (niveau 3) C4474|'*fonction*' : trop d’arguments passés pour la chaîne de format|
|Avertissement du compilateur (niveau 3) C4475|'*fonction*' : modificateur de longueur '*modificateur*'ne peut pas être utilisé avec le caractère de champ de type'*caractère*' spécificateur de format|
|Avertissement du compilateur (niveau 3) C4476|'*fonction*' : caractère de champ de type inconnu '*caractère*' spécificateur de format|
|[Avertissement du compilateur (niveau 1) C4477](c4477.md)|'*fonction*' : chaîne de format '*chaîne*'requiert un argument de type'*type*', mais l’argument variadique *nombre* a le type '*type*'|
|Avertissement du compilateur (niveau 1) C4478|'*fonction*' : Impossible de mélanger des espaces réservés positionnels et non positionnels dans la même chaîne de format|
|Avertissement C4480 de (erreur)|extension non standard utilisée : spécification du type sous-jacent pour enum '*énumération*'|
|[Avertissement du compilateur (niveau 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|extension non standard utilisée : spécificateur de substitution '*mot clé*'|
|Avertissement C4482 du compilateur|extension non standard utilisée : enum '*énumération*' utilisé dans le nom qualifié|
|Avertissement du compilateur (niveau 1, erreur) C4483|Erreur de syntaxe : mot clé C++ attendu|
|[Avertissement (erreur) du compilateur C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*fonction_substitution*' : méthode de classe ref de base correspond à «*fonction_classe_base*', mais n’est ne pas marqué comme 'virtual', 'new' ou 'override' ; 'new' (et non 'virtual') sont supposé.|
|[Avertissement (erreur) du compilateur C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*fonction_substitution*' : méthode de classe ref de base correspond à «*fonction_classe_base*', mais n’est pas marqué comme 'new' ou 'override' ; 'new' (et 'virtual') sont supposés.|
|[Avertissement du compilateur (niveau 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*fonction*' : une méthode virtuelle privée d’une classe ref ou d’une classe value doit être marquée comme 'sealed'|
|[Avertissement du compilateur (niveau 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*fonction_classe_dérivée*' : correspond à une méthode non virtuelle héritée '*fonction_classe_base*' mais n’est ne pas explicitement marqué comme 'new'|
|[Avertissement du compilateur (niveau 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*fonction*' : requiert '*mot clé*'mot clé pour implémenter la méthode d’interface'*méthode_interface*'|
|[Avertissement du compilateur (niveau 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*spécificateur*' : non autorisé sur une méthode d’interface '*méthode*' ; spécificateurs sont autorisés uniquement sur les méthodes de classe ref classe et la valeur de remplacement|
|[Avertissement du compilateur (niveau 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override' : utilisation incorrecte du spécificateur de substitution ; '*fonction*' ne correspond pas à une méthode de classe ref de base|
|Avertissement du compilateur (niveau 1) C4491|'*nom*' : a un format de version IDL non conforme|
|Avertissement du compilateur (niveau 1, erreur) C4492|'*fonction1*' : méthode de classe ref de base correspond à «*fonction2*', mais n’est ne pas marqué 'override'|
|Avertissement du compilateur (niveau 3, erreur) C4493|expression de suppression n’a aucun effet car le destructeur de '*type*' n’a pas d’accessibilité 'public'|
|Avertissement du compilateur (niveau 1) C4494|'*fonction*' : ignoré __declspec (allocateur) car le type de retour de la fonction n’est pas un pointeur ou une référence|
|Avertissement C4495 du compilateur|extension non standard '__super' utilisée : Remplacez par le nom de la classe de base explicite|
|Avertissement C4496 du compilateur|extension non standard 'for each' utilisée : Remplacez par une instruction ranged-for|
|Avertissement C4497 du compilateur|extension non standard 'sealed' utilisée : Remplacez-la par 'final'|
|Avertissement C4498 du compilateur|extension non standard utilisée : '*extension*'|
|Avertissement du compilateur (niveau 4) C4499|«*fonction*' : une spécialisation explicite ne peut pas avoir une classe de stockage (ignorée) »|
|[Avertissement du compilateur (niveau 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*spécification de liaison*' requiert l’utilisation du mot clé 'extern' et doit précéder tous les autres spécificateurs|
|[Avertissement du compilateur (niveau 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identificateur*' : nom longueur décoré dépassée, nom a été tronqué.|
|[Avertissement du compilateur (niveau 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*fonction*' : fonction locale non référencée a été supprimée.|
|[Avertissement du compilateur (niveau 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|aucune définition pour la fonction inline '*fonction*'|
|[Avertissement du compilateur (niveau 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*fonction*' : fonction doit retourner une valeur ; 'void' pris par défaut de type de retour|
|Avertissement C4509 du compilateur|extension non standard utilisée : '*fonction*' utilise SEH et '*objet*' a un destructeur|
|[Avertissement du compilateur (niveau 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*classe*' : constructeur par défaut a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*classe*' : constructeur de copie a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*classe*' : opérateur d’assignation a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*classe*' : destructeur a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*fonction*' : fonction inline non référencée a été supprimée.|
|[Avertissement du compilateur (niveau 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*espace de noms*' : espace de noms s’utilise lui-même|
|[Avertissement du compilateur (niveau 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'class::symbol' : les déclarations d’accès sont déconseillées ; déclarations using de membres constituent un meilleur choix|
|[Avertissement du compilateur (niveau 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|les déclarations d’accès sont déconseillées ; déclarations using de membres constituent un meilleur choix|
|[Avertissement du compilateur (niveau 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*spécificateur*' : classe de stockage ou de type inattendu ; ignoré|
|Avertissement (erreur) C4519 du compilateur|arguments template par défaut sont autorisés uniquement sur un modèle de classe|
|[Avertissement du compilateur (niveau 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*classe*' : plusieurs constructeurs de copie spécifiés|
|[Avertissement du compilateur (niveau 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*classe*' : plusieurs opérateurs d’assignation spécifiés|
|[Avertissement du compilateur (niveau 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*classe*' : plusieurs destructeurs spécifiés|
|[Avertissement du compilateur (niveau 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*fonction*' : fonction membre statique ne peut pas substituer la fonction virtuelle '*fonction virtuelle*' substitution ignorée, fonction virtual sera masquée|
|[Avertissement du compilateur (niveau 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Gestionnaire d’exceptions C++ utilisé, mais les sémantiques de déroulement ne sont pas activés. Spécifiez /EHsc|
|Avertissement du compilateur (niveau 1) C4531|Gestion des exceptions C++ non disponible sous Windows CE. Utilisez la gestion structurée des exceptions|
|[Avertissement du compilateur (niveau 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue' : saut hors du bloc ' __finally/finally' a un comportement indéfini lors de la gestion de l’arrêt|
|[Avertissement du compilateur (niveau 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|l’initialisation de '*variable*'est ignorée par'*étiquette goto*'|
|[Avertissement du compilateur (niveau 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*constructeur*'sera pas un constructeur par défaut pour 'class/struct' '*identificateur*' en raison de l’argument par défaut|
|[Avertissement du compilateur (niveau 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|appel de _set_se_translator() requiert /EHa|
|[Avertissement du compilateur (niveau 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*' : nom de type dépasse la limite métadonnées de '*character_limit*' caractères|
|[Avertissement du compilateur (niveau 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*objet*' : '.' appliqué à un type non UDT|
|[Avertissement du compilateur (niveau 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*type*' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.|
|[Avertissement du compilateur (niveau 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|utilisé de dynamic_cast pour convertir une base ambiguë ou inaccessible ; test d’exécution échouera ('*type1*'à'*type2*')|
|[Avertissement du compilateur (niveau 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*identificateur*'utilisé sur un type polymorphe'*type*' avec/GR- ; peut entraîner un comportement imprévisible|
|Avertissement du compilateur (niveau 1) C4542|Génération ignorée du fichier texte injecté fusionné, Impossible d’écrire *filetype* fichier : '*problème*' : *message*|
|[Avertissement du compilateur (niveau 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Injecté supprimé par l’attribut de texte « aucune\_injected_text'|
|[Avertissement du compilateur (niveau 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*déclaration*' : argument template ignoré sur cette déclaration de modèle par défaut|
|[Avertissement du compilateur (niveau 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|l’expression avant la virgule correspond à une fonction qui n’a pas de liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|l’appel de fonction avant la virgule n’a pas de liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*opérateur*' : opérateur avant la virgule n’a pas d’effet ; opérateur avec effet secondaire attendu|
|[Avertissement du compilateur (niveau 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|l'expression avant la virgule n'a pas d'effet ; expression avec effet secondaire attendu|
|[Avertissement du compilateur (niveau 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*opérateur*' : opérateur avant la virgule n’a aucun effet ; souhaitiez-vous '*opérateur*' ?|
|[Avertissement du compilateur (niveau 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|expression correspond à une fonction qui n’a pas une liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|liste d’arguments de fonction appel manquant|
|[Avertissement du compilateur (niveau 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*opérateur*' : opérateur n’a aucun effet ; opérateur avec effet secondaire attendu|
|[Avertissement du compilateur (niveau 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*opérateur*' : opérateur sans effet ; souhaitiez-vous ' opérateur ?|
|[Compilateur avertissement (niveau 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*opérateur*' : Vérifiez la priorité des opérateurs pour erreur possible ; utilisez des parenthèses pour clarifier la priorité|
|[Avertissement du compilateur (niveau 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|l'expression n'a pas d'effet ; attendue expression avec effets secondaires|
|[Avertissement du compilateur (niveau 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|valeur d’argument immédiat intrinsèque '*valeur*'est hors limites'*lower_bound* - *upper_bound*'|
|[Avertissement du compilateur (niveau 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|'__assume' contient l’effet '*effet*'|
|[Avertissement du compilateur (niveau 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|valeur de l’opérande '*valeur*'est hors limites'*lower_bound* - *upper_bound*'|
|[Avertissement du compilateur (niveau 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*fonction*' : redéfinition ; la __declspec (modifier) les gains de fonction|
|[Avertissement du compilateur (niveau 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|'__fastcall' incompatible avec le ' / clr' option : conversion en '__stdcall'|
|Avertissement du compilateur (niveau 4) C4562|fonctions entièrement prototypées sont requises avec le ' / clr' option : conversion de '()' en '(void)'|
|[Avertissement du compilateur (niveau 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|méthode '*méthode*'de 'classe' '*classname*'définit le paramètre par défaut non pris en charge'*paramètre*'|
|[Avertissement du compilateur (niveau 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*fonction*' : redéfinition ; le symbole était déclaré précédemment avec __declspec (modifier)|
|[Avertissement du compilateur (niveau 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|caractère représenté par le nom de caractère universel '*char*' ne peut pas être représenté dans la page de codes actuelle (*numéro*)|
|Avertissement du compilateur (niveau 1) C4568|'*fonction*' : aucun membre ne correspond à la signature de la substitution explicite|
|Avertissement du compilateur (niveau 3) C4569|'*fonction*' : aucun membre ne correspond à la signature de la substitution explicite|
|[Avertissement du compilateur (niveau 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*type*' : n’est pas explicitement déclaré comme abstract mais comporte des fonctions abstract|
|[Avertissement du compilateur (niveau 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Information : la sémantique changée depuis Visual C++ 7.1 ; les exceptions structurées (SEH) ne sont plus interceptées|
|[Avertissement du compilateur (niveau 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|L’attribut [ParamArray] est déconseillé sous/CLR, utilisez '...' à la place|
|Avertissement du compilateur (niveau 1) C4573|l’utilisation de '*fonction lambda*' requiert le compilateur capture 'this' mais le mode de capture par défaut actuelle ne le permet pas|
|Avertissement du compilateur (niveau 4) C4574|'*Identificateur*'n’est défini comme étant ' 0' : souhaitiez-vous utiliser 'identificateur #if' ?|
|Avertissement du compilateur (niveau 1) C4575|'__vectorcall' incompatible avec le ' / clr' option : conversion en '__stdcall'|
|Avertissement du compilateur (niveau 1, erreur) C4576|un type entre parenthèses suivi d’une liste d’initialiseurs est une syntaxe de conversion de type explicite non standard|
|Avertissement du compilateur (niveau 1, Off) C4577|'noexcept' utilisé avec aucun spécifié ; le mode de gestion des exceptions arrêt sur l’exception n’est pas garantie. Spécifiez /EHsc|
|Avertissement du compilateur (niveau 1, erreur) C4578|'abs' : conversion de '*type1*'à'*type2*', perte possible de données (souhaitiez-vous appeler '*fonction*' ou à #include \<cmath > ?)|
|[Avertissement du compilateur (niveau 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] est déconseillé ; spécifiez System::Attribute ou Platform::Metadata comme classe de base à la place|
|[Avertissement du compilateur (niveau 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportement déconseillé : ' «*chaîne*« ' remplacé par '*chaîne*' pour traiter l’attribut|
|Avertissement du compilateur (niveau 4) C4582|'*type*' : constructeur n’est pas appelé de manière implicite|
|Avertissement du compilateur (niveau 4) C4583|'*type*' : destructeur n’est pas appelé de manière implicite|
|[Avertissement du compilateur (niveau 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*' : classe de base*classe2*'est déjà une classe de base de'*class3*'|
|Avertissement du compilateur (niveau 1, erreur) C4585|'*classe*' : WinRT A 'public ref class' doit être sealed ou dériver à partir d’un fichier de classe déverrouillée|
|Avertissement du compilateur (niveau 1, erreur) C4586|'*type*' : un type public ne peut pas être déclaré dans un espace de noms de niveau supérieur appelé 'Windows'|
|Avertissement du compilateur (niveau 1) C4587|'*anonymous_structure*' : changement de comportement : constructeur est appelé n’est plus implicitement.|
|Avertissement du compilateur (niveau 1) C4588|'*anonymous_structure*' : changement de comportement : destructeur est appelé n’est plus implicitement.|
|Avertissement du compilateur (niveau 1) C4591|limite de profondeur des appels 'constexpr' de *nombre* dépassée (/ constexpr : Depth\<nombre >)|
|Avertissement du compilateur (niveau 3) C4592|'*fonction*' : Échec de l’évaluation d’appel 'constexpr' ; la fonction est appelée au moment de l’exécution|
|Avertissement du compilateur (niveau 1) C4593|'*fonction*' : limite d’étape d’évaluation d’appels 'constexpr' de '*limite*' dépassée ; utiliser/constexpr : Steps\<nombre > pour augmenter la limite|
|Avertissement du compilateur (niveau 3) C4594|'*type*' : destructeur ne sera pas implicitement appelé si une exception est levée.|
|Avertissement du compilateur (niveau 1) C4595|'*type*' : changement de comportement : destructeur ne sera n’est plus implicitement appelé si une exception est levée.|
|Avertissement du compilateur (niveau 4) C4596|'*identificateur*' : nom qualifié non conforme dans une déclaration de membre|
|Avertissement du compilateur (erreur) C4597|un comportement indéfini : offsetof appliqué à un membre de base virtuelle|
|Avertissement du compilateur (niveaux 1 et 3) C4598|' #include «*en-tête*» ' : numéro de l’en-tête *nombre* dans l’en-tête précompilé ne correspond pas à la compilation en cours à cette position|
|Avertissement du compilateur (niveau 3) C4599|'*indicateur* *chemin d’accès*' : nombre d’arguments de ligne de commande *nombre* ne correspond pas d’en-tête précompilé|
