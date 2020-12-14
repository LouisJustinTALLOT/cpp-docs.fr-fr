---
description: 'En savoir plus sur les éléments suivants : avertissements du compilateur C4400 à C4599'
title: Avertissements du compilateur C4400 à C4599
ms.date: 04/21/2019
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
- C4452
- C4453
- C4454
- C4455
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
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: e3c182439d03fdefa476231f871c60d3d297a037
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212023"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Avertissements du compilateur C4400 à C4599

Les Articles de cette section de la documentation expliquent un sous-ensemble de messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Avertissement|Message|
|-------------|-------------|
|[Avertissement du compilateur (niveau 1) C4600](compiler-warning-level-1-c4600.md)|#pragma'*nom de macro*' : chaîne non vide valide attendue|
|[Avertissement du compilateur (niveau 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*type*' : les qualificateurs const/volatile sur ce type ne sont pas pris en charge|
|[Avertissement du compilateur (niveau 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*champ de bits' :* le membre est un champ de bits|
|[Avertissement du compilateur (niveau 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|doit utiliser l’opérateur PTR|
|[Avertissement du compilateur (niveau 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|opérateur PTR non conforme|
|[Avertissement du compilateur (niveau 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|période sur la directive ignorée|
|[Avertissement du compilateur (niveau 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identificateur*' : l’identificateur est un mot réservé|
|[Avertissement du compilateur (niveau 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|opérande sur directive ignoré|
|[Avertissement du compilateur (niveau 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|Cast entre différentes représentations de pointeur vers membre, le compilateur peut générer du code incorrect|
|[Avertissement du compilateur (niveau 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|'struct&#124;Union’anonyme n’a déclaré aucune donnée membre|
|[Avertissement du compilateur (niveau 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|taille d’instruction non conforme|
|[Avertissement du compilateur (niveau 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|taille non conforme pour l’opérande|
|[Avertissement du compilateur (niveau 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identificateur*' : le symbole se résout en registre de déplacement|
|[Avertissement du compilateur (niveau 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*fonction*' : la signature de fonction contient le type'*type*'; Les objets C++ ne sont pas sûrs à passer entre le code pur et le code mixte ou natif.|
|Avertissement du compilateur C4413|'ClassName :: Member' : le membre de référence est initialisé à un temporaire qui ne persiste pas après la sortie du constructeur|
|[Avertissement du compilateur (niveau 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*fonction*' : saut court à la fonction converti en Near|
|Avertissement du compilateur (niveau 1) C4415|__declspec dupliqué (code_seg ('*Name*'))|
|Avertissement du compilateur (niveau 1) C4416|__declspec (code_seg (...)) contient une chaîne vide : ignoré|
|Avertissement du compilateur (niveau 1) C4417|une instanciation de modèle explicite ne peut pas avoir __declspec (code_seg (...)) : ignoré|
|Avertissement du compilateur (niveau 1) C4418|__declspec (code_seg (...)) ignoré sur une énumération|
|Avertissement du compilateur (niveau 3) C4419|'*symbol*'n’a aucun effet lorsqu’il est appliqué à la classe ref privée'*Class*'.|
|[Avertissement du compilateur (niveau 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*' : opérateur non disponible, en utilisant'*opérateur*'à la place ; la vérification au moment de l’exécution peut être compromise|
|Avertissement du compilateur (niveau 3) C4421|'*paramètre*' : un paramètre de référence sur une fonction pouvant être reprise est potentiellement dangereux|
|Avertissement du compilateur (niveau 3) C4423|'std :: bad_alloc' : sera intercepté par la classe ('*type*') sur le *numéro* de ligne|
|Avertissement du compilateur (niveau 3) C4424|catch pour «*type1*» précédé de «*type2*» sur le *numéro* de ligne ; un comportement imprévisible peut se produire si’std :: bad_alloc’est levé|
|Avertissement du compilateur (niveau 1) C4425|Une annotation SAL ne peut pas être appliquée à'... '|
|Avertissement du compilateur (niveau 1) C4426|indicateurs d’optimisation modifiés après l’ajout de l’en-tête, peut être dû à #pragma optimiser ()|
|Avertissement du compilateur (niveau 1) C4427|'*opérateur*' : dépassement de capacité de la Division constante, comportement non défini|
|[Avertissement du compilateur (niveau 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|nom de caractère universel éventuellement incomplet ou incorrect|
|[Avertissement du compilateur (erreur) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut|
|[Avertissement du compilateur (niveau 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut|
|[Avertissement du compilateur (niveau 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|un constructeur statique doit avoir un accès privé ; passage à l’accès privé|
|[Avertissement du compilateur (niveau 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*Derived_Class*' : la disposition des objets sous/VD2 sera modifiée en raison de la base virtuelle'*BASE_CLASS*'|
|[Avertissement du compilateur (niveau 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|le \_ Cast dynamique de la base virtuelle'*BASE_CLASS*'en'*Derived_Class*'dans le constructeur ou le destructeur peut échouer avec un objet partiellement construit|
|[Avertissement du compilateur (niveau 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|\_la conversion dynamique de la base virtuelle'*BASE_CLASS*'en'*Derived_Class*'peut échouer dans certains contextes|
|Avertissement du compilateur C4438|'*fonction*' : ne peut pas être appelé en toute sécurité dans/await : mode clrcompat. Si'*Function*'appelle le CLR, cela peut entraîner une altération de la tête CLR|
|[Avertissement du compilateur (erreur) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*fonction*' : la définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall|
|[Avertissement du compilateur (niveau 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|redéfinition de la Convention d’appel de'*calling_convention1*'à'*calling_convenction2*'ignorée|
|[Avertissement du compilateur (niveau 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|Convention d’appel de'*calling_convention1*'ignorée ; '*calling_convention2*'utilisé à la place|
|Avertissement du compilateur (niveau 1) C4442|terminateur null incorporé dans __annotation argument.  La valeur sera tronquée.|
|Avertissement du compilateur (niveau 1) C4443|le paramètre pragma attendu doit être' 0 ', ' 1 'ou' 2 '|
|Avertissement du compilateur (niveau 3) C4444|'*identificateur*' : le niveau supérieur' __unaligned’n’est pas implémenté dans ce contexte|
|[Avertissement du compilateur (niveau 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*fonction*' : dans un type’managed&#124;'WinRT', une méthode virtuelle ne peut pas être privée|
|Avertissement du compilateur (niveau 1) C4446|'*type*' : impossible de mapper le membre'*nom1*'dans ce type, en raison d’un conflit avec le nom de type. La méthode a été renommée en «*nom2*»|
|Avertissement du compilateur (niveau 1) C4447|signature’main’trouvée sans modèle de thread. Envisagez d’utiliser’int main (Platform :: array \<Platform::String^> ^ args) '.|
|Avertissement du compilateur C4448|'*type* 1 'n’a pas d’interface par défaut spécifiée dans les métadonnées. Sélection : '*type2*', qui peut échouer au moment de l’exécution.|
|Avertissement du compilateur C4449|'*type*'un type non scellé doit être marqué en tant que' [WebHostHidden] '|
|Avertissement du compilateur C4450|'*type1*'doit être marqué en tant que' [WebHostHidden] ', car il dérive de'*type2*'|
|Avertissement du compilateur (niveau 4) C4451|'classname1 :: Member' : l’utilisation de la classe ref’classname2 :: Member’dans ce contexte peut entraîner un marshaling d’objet non valide dans les contextes|
|Avertissement du compilateur (niveau 1) C4452|'*identificateur*' : le type public ne peut pas être au niveau de la portée globale. Il doit se trouver dans un espace de noms qui est un enfant du nom du fichier. winmd de sortie.|
|Avertissement du compilateur (niveau 1) C4453|'*type*' : un type' [WebHostHidden] 'ne doit pas être utilisé sur la surface publiée d’un type public qui n’est pas' [WebHostHidden] '|
|Avertissement du compilateur (niveau 1) C4454|'*fonction*'est surchargé par plus que le nombre de paramètres d’entrée sans que [DefaultOverload] ne soit spécifié. Sélection de «*déclaration*» comme surcharge par défaut|
|Avertissement du compilateur (niveau 1) C4455|'operator *opérateur*' : les identificateurs de suffixe littéral qui ne commencent pas par un trait de soulignement sont réservés|
|[Avertissement du compilateur (niveau 4) C4456](compiler-warning-level-4-c4456.md)|la déclaration de'*identifier*'masque la déclaration locale précédente|
|[Avertissement du compilateur (niveau 4) C4457](compiler-warning-level-4-c4457.md)|la déclaration de'*identifier*'masque le paramètre de fonction|
|[Avertissement du compilateur (niveau 4) C4458](compiler-warning-level-4-c4458.md)|la déclaration de'*identifier*'masque le membre de classe|
|[Avertissement du compilateur (niveau 4) C4459](compiler-warning-level-4-c4459.md)|la déclaration de'*identifier*'masque la déclaration globale|
|[Avertissement du compilateur (niveau 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|Le paramètre’opérateur’WinRT&#124;géré *'opérateur'* possède un paramètre passé par référence. 'L'*opérateur' '* opérateur’de gestion de&#124;WinRT a une sémantique différente de celle de l’opérateur C++ '*cpp_operator*'. voulez-vous passer par valeur ?|
|[Avertissement du compilateur (niveau 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*className*' : cette classe a un finaliseur' ! ' *finaliseur*'mais aucun destructeur' ~*dtor*'|
|[Avertissement du compilateur (niveau 1, erreur) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*type*' : impossible de déterminer le GUID du type. Le programme risque d'échouer au moment de l'exécution.|
|[Avertissement du compilateur (niveau 4) C4463](compiler-warning-level-4-c4463.md)|surcharge assignation de'*value*'à un champ de bits qui ne peut contenir que des valeurs de'*MIN_VALUE*'à'*MAX_VALUE*'|
|[Avertissement du compilateur (niveau 4) C4464](../../error-messages/compiler-warnings/c4464.md)|le chemin d’accès include relatif contient'.. '|
|[Avertissement du compilateur (niveau 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de contrôle à virgule flottante ignorés sous/CLR|
|[Avertissement du compilateur (niveau 4) C4471](compiler-warning-level-4-c4471.md)|'*énumération*' : une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int pris par défaut)|
|Avertissement du compilateur (niveau 1) C4472|'*identifier*'est un enum natif : ajoutez un spécificateur d’accès (Private/Public) pour déclarer une énumération’WinRT&#124;Managed'|
|[Avertissement du compilateur (niveau 1) C4473](c4473.md)|'*fonction*' : nombre insuffisant d’arguments passés pour la chaîne de format|
|Avertissement du compilateur (niveau 3) C4474|'*fonction*' : trop d’arguments passés pour la chaîne de format|
|Avertissement du compilateur (niveau 3) C4475|'*fonction*' : le modificateur de longueur'*modifier*'ne peut pas être utilisé avec le caractère de champ de type'*caractère*'dans le spécificateur de format|
|Avertissement du compilateur (niveau 3) C4476|'*fonction*' : caractère de champ de type inconnu'*caractère*'dans le spécificateur de format|
|[Avertissement du compilateur (niveau 1) C4477](c4477.md)|'*fonction*' : la chaîne de mise en forme'*chaîne*'requiert un argument de type'*type*', mais le *numéro* d’argument variadiques a le type'*type*'|
|Avertissement du compilateur (niveau 1) C4478|'*fonction*' : les espaces réservés positionnels et non positionnels ne peuvent pas être mélangés dans la même chaîne de format|
|Avertissement du compilateur (erreur) C4480|extension non standard utilisée : spécification du type sous-jacent pour l'*énumération’Enumeration*'|
|[Avertissement du compilateur (niveau 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|extension non standard utilisée : spécificateur de substitution'*Keyword*'|
|Avertissement du compilateur C4482|extension non standard utilisée : enum'*Enumeration*'utilisé dans le nom qualifié|
|Avertissement du compilateur (niveau 1, erreur) C4483|erreur de syntaxe : mot clé C++ ATTENDU|
|[Avertissement du compilateur (erreur) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*' : correspond à la méthode de classe ref de base'*base_class_function*', mais n’est pas marqué comme’Virtual', 'New’ou’override'; 'New' (et non’Virtual') est pris par défaut|
|[Avertissement du compilateur (erreur) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*' : correspond à la méthode de classe ref de base'*base_class_function*', mais n’est pas marqué comme’New’ou’override'; 'New' (et’Virtual') est pris par défaut|
|[Avertissement du compilateur (niveau 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*fonction*' : une méthode virtuelle privée d’une classe ref ou d’une classe value doit être marquée comme’sealed'|
|[Avertissement du compilateur (niveau 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*' : correspond à la méthode non virtuelle héritée'*base_class_function*'mais n’est pas explicitement marquée comme’New'|
|[Avertissement du compilateur (niveau 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*fonction*' : requiert le mot clé'*Keyword*'pour implémenter la méthode d’interface'*interface_method*'|
|[Avertissement du compilateur (niveau 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*specifier*' : non autorisé sur la méthode d’interface'*méthode*'; les spécificateurs de substitution sont uniquement autorisés sur les méthodes de classe ref et de classe value|
|[Avertissement du compilateur (niveau 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override' : utilisation incorrecte du spécificateur de substitution ; '*Function*'ne correspond pas à une méthode de classe ref de base|
|Avertissement du compilateur (niveau 1) C4491|'*Name*' : format de version IDL non conforme|
|Avertissement du compilateur (niveau 1, erreur) C4492|'*fonction1*' : correspond à la méthode de classe ref de base'*fonction2*', mais n’est pas marqué comme’override'|
|Avertissement du compilateur (niveau 3, erreur) C4493|l’expression Delete n’a aucun effet, car le destructeur de'*type*'n’a pas d’accessibilité’public'|
|Avertissement du compilateur (niveau 1) C4494|'*fonction*' : __declspec ignorée (Allocator), car le type de retour de la fonction n’est pas un pointeur ni une référence|
|Avertissement du compilateur C4495|extension non standard' __super’utilisée : remplacez par le nom de la classe de base explicite|
|Avertissement du compilateur C4496|extension non standard’for each’utilisée : remplacer par l’instruction rangeed-for|
|Avertissement du compilateur C4497|extension non standard’sealed’utilisée : remplacez par’final'|
|Avertissement du compilateur C4498|extension non standard utilisée : '*extension*'|
|Avertissement du compilateur (niveau 4) C4499|'*fonction*' : une spécialisation explicite ne peut pas avoir de classe de stockage (ignorée) "|
|[Avertissement du compilateur (niveau 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*Linking Specification*'nécessite l’utilisation du mot clé’extern’et doit précéder tous les autres spécificateurs|
|[Avertissement du compilateur (niveau 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identificateur*' : longueur du nom décoré dépassée, le nom a été tronqué|
|[Avertissement du compilateur (niveau 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*fonction*' : la fonction locale non référencée a été supprimée|
|[Avertissement du compilateur (niveau 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|aucune définition pour la fonction inline'*fonction*'|
|[Avertissement du compilateur (niveau 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*fonction*' : la fonction doit retourner une valeur ; type de retour’void’pris par défaut|
|Avertissement du compilateur C4509|extension non standard utilisée : '*fonction*'utilise SEH et'*objet*'a un destructeur|
|[Avertissement du compilateur (niveau 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*classe*' : le constructeur par défaut a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*classe*' : le constructeur de copie a été implicitement défini comme étant supprimé|
|[Avertissement du compilateur (niveau 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*classe*' : l’opérateur d’assignation a été défini de manière implicite comme supprimé|
|[Avertissement du compilateur (niveau 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*classe*' : le destructeur a été défini de manière implicite comme supprimé|
|[Avertissement du compilateur (niveau 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*fonction*' : la fonction inline non référencée a été supprimée|
|[Avertissement du compilateur (niveau 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*namespace*' : l’espace de noms s’utilise lui-même|
|[Avertissement du compilateur (niveau 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'Class :: Symbol' : les déclarations d’accès sont déconseillées ; les déclarations using de membre offrent une meilleure alternative|
|[Avertissement du compilateur (niveau 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|les déclarations d’accès sont déconseillées ; les déclarations using de membre offrent une meilleure alternative|
|[Avertissement du compilateur (niveau 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*specifier*' : classe de stockage ou spécificateur (s) de type inattendu (e) ici ; pas|
|Avertissement du compilateur (erreur) C4519|les arguments template par défaut sont autorisés uniquement sur un modèle de classe|
|[Avertissement du compilateur (niveau 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*classe*' : plusieurs constructeurs de copie spécifiés|
|[Avertissement du compilateur (niveau 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*classe*' : plusieurs opérateurs d’assignation spécifiés|
|[Avertissement du compilateur (niveau 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*classe*' : plusieurs destructeurs spécifiés|
|[Avertissement du compilateur (niveau 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*fonction*' : la fonction membre statique ne peut pas substituer la fonction virtuelle'*fonction virtuelle*'override ignorée, la fonction Virtual sera masquée|
|[Avertissement du compilateur (niveau 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Le gestionnaire d’exceptions C++ est utilisé, mais les sémantiques de déroulement ne sont pas activées. Spécifier/EHsc|
|Avertissement du compilateur (niveau 1) C4531|La gestion des exceptions C++ n’est pas disponible sur Windows CE. Utiliser la gestion structurée des exceptions|
|[Avertissement du compilateur (niveau 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue' : le saut hors du bloc' __finally/finally’a un comportement indéfini lors de la gestion de l’arrêt|
|[Avertissement du compilateur (niveau 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|l’initialisation de'*variable*'est ignorée par'*goto label*'|
|[Avertissement du compilateur (niveau 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*constructor*'ne sera pas un constructeur par défaut pour’class/struct' '*identifier*'en raison de l’argument par défaut|
|[Avertissement du compilateur (niveau 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|l’appel de _set_se_translator () requiert/EHa|
|[Avertissement du compilateur (niveau 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*TypeName*' : le nom de type dépasse la limite de métadonnées de'*character_limit*'caractères|
|[Avertissement du compilateur (niveau 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*objet*' : '. 'appliqué à un type non UDT|
|[Avertissement du compilateur (niveau 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*type*' : les qualificateurs const/volatile sur ce type ne sont pas pris en charge|
|[Avertissement du compilateur (niveau 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast utilisé pour la conversion en base inaccessible ou ambiguë ; le test au moment de l’exécution échoue ('*type1*'en'*type2*')|
|[Avertissement du compilateur (niveau 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*identifier*'utilisé sur le type polymorphe'*type*'avec/gr-; un comportement imprévisible peut se produire|
|Avertissement du compilateur (niveau 1) C4542|La génération du fichier texte injecté fusionné est ignorée. impossible d’écrire le fichier *filetype* : '*problème*' : *message*|
|[Avertissement du compilateur (niveau 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Texte injecté supprimé par l’attribut’no \_ injected_text'|
|[Avertissement du compilateur (niveau 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*DECLARATION*' : argument template par défaut ignoré sur cette déclaration de modèle|
|[Avertissement du compilateur (niveau 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|l’expression avant la virgule correspond à une fonction qui n’a pas de liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|l’appel de fonction avant la virgule n’a pas de liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*opérateur*' : l’opérateur avant la virgule n’a aucun effet ; opérateur avec effet secondaire ATTENDU|
|[Avertissement du compilateur (niveau 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|l'expression avant la virgule n'a pas d'effet ; expression avec effet secondaire attendu|
|[Avertissement du compilateur (niveau 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*opérateur*' : l’opérateur avant la virgule n’a aucun effet ; souhaitiez-vous'*Operator*' ?|
|[Avertissement du compilateur (niveau 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|l’expression prend la valeur d’une fonction qui n’a pas de liste d’arguments|
|[Avertissement du compilateur (niveau 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|liste d’arguments manquante dans l’appel de fonction|
|[Avertissement du compilateur (niveau 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*Operator*' : l’opérateur n’a aucun effet ; opérateur avec effet secondaire ATTENDU|
|[Avertissement du compilateur (niveau 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*Operator*' : l’opérateur n’a aucun effet ; souhaitiez-vous opérateur' ?|
|[Avertissement du compilateur (niveau 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*opérateur*' : Vérifiez la priorité des opérateurs pour déterminer si une erreur est possible ; utiliser des parenthèses pour clarifier la précédence|
|[Avertissement du compilateur (niveau 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|l'expression n'a pas d'effet ; attendue expression avec effets secondaires|
|[Avertissement du compilateur (niveau 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|la valeur de l’argument immédiat intrinsèque'*value*'est hors limites'*lower_bound*  -  *upper_bound*'|
|[Avertissement du compilateur (niveau 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|' __assume’contient l’effet *'effect'*|
|[Avertissement du compilateur (niveau 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|la valeur de l’opérande'*value*'est hors limites'*lower_bound*  -  *upper_bound*'|
|[Avertissement du compilateur (niveau 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*fonction*' : redéfinition ; la fonction gagne __declspec (modificateur)|
|[Avertissement du compilateur (niveau 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|' __fastcall’incompatible avec l’option'/CLR' : conversion en' __stdcall'|
|Avertissement du compilateur (niveau 4) C4562|des fonctions entièrement prototypées sont requises avec l’option'/CLR' : conversion de' () 'en' (void) '|
|[Avertissement du compilateur (niveau 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|la méthode'*méthode*'de’classe' '*className*'définit un paramètre par défaut non pris en charge'*Parameter*'|
|[Avertissement du compilateur (niveau 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*fonction*' : redéfinition ; le symbole a été précédemment déclaré avec __declspec (modificateur)|
|[Avertissement du compilateur (niveau 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|le caractère représenté par le nom de caractère universel'*char*'ne peut pas être représenté dans la page de codes actuelle (*nombre*)|
|Avertissement du compilateur (niveau 1) C4568|'*fonction*' : aucun membre ne correspond à la signature de la substitution explicite|
|Avertissement du compilateur (niveau 3) C4569|'*fonction*' : aucun membre ne correspond à la signature de la substitution explicite|
|[Avertissement du compilateur (niveau 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*type*' : n’est pas explicitement déclaré comme abstract, mais a des fonctions abstraites|
|[Avertissement du compilateur (niveau 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Informations : la sémantique catch (...) a changé depuis Visual C++ 7,1 ; les exceptions structurées (SEH) ne sont plus interceptées|
|[Avertissement du compilateur (niveau 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|L’attribut [ParamArray] est déconseillé sous/CLR, utilisez'... ' qu'|
|Avertissement du compilateur (niveau 1) C4573|l’utilisation de'*lambda Function*'requiert que le compilateur capture’This', mais le mode de capture par défaut actuel ne le permet pas|
|Avertissement du compilateur (niveau 4) C4574|'*Identifier*'est défini comme étant' 0 ' : vouliez-vous utiliser' #if identificateur' ?|
|Avertissement du compilateur (niveau 1) C4575|' __vectorcall’incompatible avec l’option'/CLR' : conversion en' __stdcall'|
|Avertissement du compilateur (niveau 1, erreur) C4576|un type entre parenthèses suivi d’une liste d’initialiseurs est une syntaxe de conversion de type explicite non standard|
|[Avertissement du compilateur (niveau 1, désactivé) C4577](../../error-messages/compiler-warnings/compiler-warning-level-1-c4577.md)|'noexcept’utilisé sans le mode de gestion des exceptions spécifié ; l’arrêt en cas d’exception n’est pas garanti. Spécifier/EHsc|
|Avertissement du compilateur (niveau 1, erreur) C4578|'ABS' : conversion de'*type1*'en'*type2*', perte possible de données (vouliez-vous appeler'*Function*'ou #include \<cmath> ?)|
|[Avertissement du compilateur (niveau 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] est déconseillé ; spécifiez System::Attribute ou Platform::Metadata comme classe de base à la place|
|[Avertissement du compilateur (niveau 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportement déconseillé : ' "*String*" 'remplacé par'*String*'pour traiter l’attribut|
|Avertissement du compilateur (niveau 4) C4582|'*type*' : le constructeur n’est pas appelé implicitement|
|Avertissement du compilateur (niveau 4) C4583|'*type*' : le destructeur n’est pas appelé implicitement|
|[Avertissement du compilateur (niveau 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*classe1*' : la classe de base'*Classe2*'est déjà une classe de base de'*class3*'|
|Avertissement du compilateur (niveau 1, erreur) C4585|'*classe*' : une’public ref class’WinRT doit être sealed ou dériver d’une classe unsealed existante|
|Avertissement du compilateur (niveau 1, erreur) C4586|'*type*' : un type public ne peut pas être déclaré dans un espace de noms de niveau supérieur appelé’Windows'|
|Avertissement du compilateur (niveau 1) C4587|'*anonymous_structure*' : changement de comportement : le constructeur n’est plus appelé de manière implicite|
|Avertissement du compilateur (niveau 1) C4588|'*anonymous_structure*' : changement de comportement : le destructeur n’est plus appelé de manière implicite|
|Avertissement du compilateur (niveau 1) C4591|'constexpr' : limite de profondeur de *nombre* dépassée (/constexpr : Depth \<NUMBER> )|
|Avertissement du compilateur (niveau 3) C4592|'*fonction*' : échec de l’évaluation de l’appel’constexpr'; la fonction sera appelée au moment de l’exécution|
|Avertissement du compilateur (niveau 1) C4593|'*fonction*' : la limite de l’étape d’évaluation de'*Limit*'d’appel’constexpr’est dépassée ; Utilisez/constexpr : étapes \<NUMBER> pour augmenter la limite|
|Avertissement du compilateur (niveau 3) C4594|'*type*' : le destructeur ne sera pas appelé implicitement si une exception est levée|
|Avertissement du compilateur (niveau 1) C4595|'*type*' : changement de comportement : le destructeur ne sera plus appelé implicitement si une exception est levée|
|[Avertissement du compilateur (niveau 4) C4596](../../error-messages/compiler-warnings/c4596.md)|'*identificateur*' : nom qualifié non conforme dans une déclaration de membre|
|Avertissement du compilateur (erreur) C4597|comportement non défini : OffsetOf appliqué à un membre d’une base virtuelle|
|Avertissement du compilateur (niveau 1 et niveau 3) C4598|« #include »*en-tête*«» : le *numéro* du numéro d’en-tête dans l’en-tête précompilé ne correspond pas à la compilation en cours à cette position|
|Avertissement du compilateur (niveau 3) C4599|'*Flag* *path*' : le numéro du numéro d’argument de ligne de *commande ne correspond* pas à l’en-tête précompilé|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Avertissements du compilateur C4000 - C5999](compiler-warnings-c4000-c5999.md)
