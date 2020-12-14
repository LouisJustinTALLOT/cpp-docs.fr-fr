---
description: 'En savoir plus sur les éléments suivants : avertissements du compilateur C4600 à C4799'
title: Avertissements du compilateur C4600 à C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 9290f01d24e628ead4649c28ecbfacfec0803591
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197996"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Avertissements du compilateur C4600 à C4799

Les Articles de cette section de la documentation expliquent un sous-ensemble de messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Avertissement|Message|
|-------------|-------------|
|[Avertissement du compilateur (niveau 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma’nom de macro' : chaîne non vide valide attendue|
|[Avertissement du compilateur (niveau 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro : 'nom de macro’aucun push_macro de #pragma précédent pour cet identificateur|
|[Avertissement du compilateur (niveau 1) C4603](compiler-warning-level-1-c4603.md)|'*identificateur*' : la macro n’est pas définie ou la définition est différente après l’utilisation d’un en-tête précompilé|
|Avertissement du compilateur (niveau 1) C4604|'*type*' : le passage d’un argument par valeur sur une limite native et managée nécessite un constructeur de copie valide. Dans le cas contraire, le comportement d’exécution n’est pas défini|
|Avertissement du compilateur (niveau 1) C4605|'/D *macro*'spécifié sur la ligne de commande actuelle, mais n’a pas été spécifié quand l’en-tête précompilé a été généré|
|[Avertissement du compilateur (niveau 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|AVERTISSEMENT #pragma : 'Warning Number’ignoré ; Les avertissements de l’analyse du code ne sont pas associés à des niveaux d’avertissement|
|[Avertissement du compilateur (niveau 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' a déjà été initialisé par un autre membre union dans la liste des initialiseurs, 'union_member'|
|Avertissement du compilateur (niveau 3, erreur) C4609|'*type1*'dérive de l’interface par défaut'*interface*'sur le type'*type2*'. Utilisez une autre interface par défaut pour'*type1*', ou rompez la relation de base/dérivée.|
|[Avertissement du compilateur (niveau 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|l’objet’class’ne peut jamais être instancié-constructeur défini par l’utilisateur requis|
|[Avertissement du compilateur (niveau 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|l’interaction entre’Function’et la destruction d’objet C++ n’est pas portable|
|[Avertissement du compilateur (niveau 1) C4612](compiler-warning-level-1-c4612.md)|erreur dans le nom de fichier Include|
|[Avertissement du compilateur (niveau 1) C4613](compiler-warning-level-1-c4613.md)|'*symbol*' : la classe du segment ne peut pas être modifiée|
|[Avertissement du compilateur (niveau 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|AVERTISSEMENT #pragma : type d’avertissement utilisateur inconnu|
|[Avertissement du compilateur (niveau 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma AVERTISSEMENT : le numéro d’avertissement’numéro’n’est pas un avertissement de compilateur valide|
|[Avertissement du compilateur (niveau 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|les paramètres pragma comportaient une chaîne vide ; pragma ignoré|
|[Avertissement du compilateur (niveau 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning : numéro d'avertissement inexistant 'numéro'|
|[Avertissement du compilateur (niveau 1) C4620](compiler-warning-level-1-c4620.md)|aucune forme suffixée de l’opérateur 'operator ++' trouvée pour le type 'type' ; utilisez la forme préfixée|
|[Avertissement du compilateur (niveau 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|aucune forme suffixée de’operator--'trouvée pour le type’type', à l’aide d’une forme de préfixe|
|[Avertissement du compilateur (niveau 3) C4622](compiler-warning-level-3-c4622.md)|remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'|
|[Avertissement du compilateur (niveau 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'classe dérivée' : le constructeur par défaut a été défini de manière implicite comme supprimé, car un constructeur par défaut de la classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'classe dérivée' : le destructeur a été défini de manière implicite comme supprimé, car un destructeur de classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'classe dérivée' : le constructeur de copie a été défini de manière implicite comme supprimé, car un constructeur de copie de classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'classe dérivée' : l’opérateur d’assignation a été défini de manière implicite comme supprimé, car un opérateur d’assignation de la classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|' \<identifier> ' : ignoré lors de la recherche d’une utilisation d’en-tête précompilé|
|[Avertissement du compilateur (niveau 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|digrammes non pris en charge avec -Ze. Séquence de caractères’digramme’non interprétée comme jeton de remplacement pour'% s'|
|[Avertissement du compilateur (niveau 4) C4629](compiler-warning-level-4-c4629.md)|digrammes utilisés, séquence de caractères 'digramme' interprétée comme jeton 'caractère' (insérez un espace entre les deux caractères si cela n’est pas ce que vous souhaitiez)|
|[Avertissement du compilateur (niveau 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'Symbol' : spécificateur de classe de stockage’extern’non conforme sur la définition de membre|
|Avertissement du compilateur (niveau 2) C4631|MSXML ou XPath non disponible, les commentaires de document XML ne seront pas traités. reason|
|[Avertissement du compilateur (niveau 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Commentaire de document XML : fichier-accès refusé : raison|
|[Avertissement du compilateur (niveau 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Cible de commentaire de document XML : erreur : raison|
|[Avertissement du compilateur (niveau 4) C4634](compiler-warning-level-4-c4634.md)|Cible de commentaire de document XML : ne peut pas être appliqué : raison|
|[Avertissement du compilateur (niveau 3) C4635](compiler-warning-level-3-c4635.md)|Cible de commentaire de document XML : code XML incorrect : raison|
|[Avertissement du compilateur (niveau 3) C4636](compiler-warning-level-3-c4636.md)|Commentaire de document XML appliqué à Construct : la balise requiert un attribut’Attribute’non vide.|
|[Avertissement du compilateur (niveau 3 et niveau 4) C4637](compiler-warning-level-3-c4637.md)|Cible de commentaire de document XML : \<include> balise ignorée. Motif|
|[Avertissement du compilateur (niveau 3) C4638](compiler-warning-level-3-c4638.md)|Cible de commentaire de document XML : référence à un symbole inconnu’Symbol'.|
|[Avertissement du compilateur (niveau 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Erreur MSXML, les commentaires de document XML ne seront pas traités. Motif|
|[Avertissement du compilateur (niveau 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance' : la construction d'un objet static local n'est pas thread-safe|
|[Avertissement du compilateur (niveau 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Le commentaire de document XML comporte une référence croisée ambiguë :|
|[Avertissement du compilateur (niveau 3) C4645](compiler-warning-level-3-c4645.md)|la fonction déclarée avec __declspec(noreturn) a une instruction return|
|[Avertissement du compilateur (niveau 3) C4646](compiler-warning-level-3-c4646.md)|la fonction déclarée avec __declspec(noreturn) a un type de retour non void|
|Avertissement du compilateur (niveau 3) C4647|changement de comportement : __is_pod (*type*) a une valeur différente dans les versions précédentes|
|Avertissement du compilateur (niveau 3) C4648|l’attribut standard’carries_dependency’est ignoré|
|Avertissement du compilateur (niveau 3) C4649|les attributs sont ignorés dans ce contexte|
|[Avertissement du compilateur (niveau 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informations de débogage absentes de l’en-tête précompilé ; Seuls les symboles globaux de l’en-tête seront disponibles|
|[Avertissement du compilateur (niveau 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|'définition’spécifié pour l’en-tête précompilé mais pas pour la compilation actuelle|
|[Avertissement du compilateur (niveau 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|option du compilateur’option’non cohérente avec l’en-tête précompilé ; l’option de ligne de commande actuelle remplace celle qui est définie dans l’en-tête précompilé|
|[Avertissement du compilateur (niveau 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|option du compilateur’option’non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours ignorée|
|Avertissement du compilateur (niveau 4) C4654|Le code placé avant l’inclusion de la ligne d’en-tête précompilé sera ignoré. Ajoutez du code à l’en-tête précompilé.|
|[Avertissement du compilateur (niveau 1) C4655](compiler-warning-level-1-c4655.md)|'Symbol' : le type de variable est nouveau depuis la dernière build, ou est défini différemment à un autre endroit|
|[Avertissement du compilateur (niveau 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'Symbol' : le type de données est nouveau ou a été modifié depuis la dernière build, ou est défini différemment ailleurs|
|[Avertissement du compilateur (niveau 1) C4657](compiler-warning-level-1-c4657.md)|l’expression implique un type de données nouveau depuis la dernière Build|
|Avertissement du compilateur (niveau 1) C4658|'fonction' : le prototype de fonction est nouveau depuis la dernière build, ou est déclaré différemment à un autre emplacement|
|[Avertissement du compilateur (niveau 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma’pragma' : l’utilisation du segment réservé’segment’a un comportement indéfini, utilisez #pragma commentaire (éditeur de liens,...)|
|[Avertissement du compilateur (niveau 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identificateur' : aucune définition appropriée fournie pour la demande d’instanciation explicite du modèle|
|[Avertissement du compilateur (niveau 1) C4662](compiler-warning-level-1-c4662.md)|instanciation explicite ; la classe de modèle 'identificateur1' n’a aucune définition pour spécialiser 'identificateur2'|
|[Avertissement du compilateur (niveau 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'fonction' : aucun modèle de fonction défini correspondant à l’instanciation forcée|
|[Avertissement du compilateur (niveau 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'Symbol’n’est pas défini en tant que macro de préprocesseur, remplaçant par' 0 'pour’directive'|
|[Avertissement du compilateur (niveau 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'Cast' : conversion risquée : 'class’est un objet de type managé|
|[Avertissement du compilateur (niveau 4) C4670](compiler-warning-level-4-c4670.md)|'identificateur' : cette classe de base est inaccessible|
|Avertissement du compilateur (niveau 4) C4671|'identificateur' : le constructeur de copie est inaccessible|
|[Avertissement du compilateur (niveau 4) C4672](compiler-warning-level-4-c4672.md)|'identificateur1 ' : ambigu. Déjà rencontré comme 'identifier2'|
|[Avertissement du compilateur (niveau 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|levée de’identifier’les types suivants ne seront pas pris en compte sur le site d’interception|
|[Avertissement du compilateur (niveau 1) C4674](compiler-warning-level-1-c4674.md)|'method' doit être déclaré 'static' et avoir un seul paramètre|
|Avertissement du compilateur (niveau 4) C4676|'% s' : le destructeur est inaccessible|
|[Avertissement du compilateur (niveau 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'fonction' : la signature d’un membre non privé contient un type privé d’assembly’private_type'|
|[Avertissement du compilateur (niveau 1) C4678](compiler-warning-level-1-c4678.md)|la classe de base 'base_type' est moins accessible que 'derived_type'|
|[Avertissement du compilateur (niveau 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'membre' : impossible d’importer le membre|
|[Avertissement du compilateur (niveau 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'classe' : la coclasse ne spécifie pas d’interface par défaut|
|[Avertissement du compilateur (niveau 4) C4681](compiler-warning-level-4-c4681.md)|'classe' : la coclasse ne spécifie pas d’interface par défaut qui est une source d’événements|
|[Avertissement du compilateur (niveau 4) C4682](compiler-warning-level-4-c4682.md)|'paramètre' : aucun attribut de paramètre directionnel spécifié, [in] par défaut|
|[Avertissement du compilateur (niveau 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'fonction' : la source de l’événement a un paramètre’out'; Soyez prudent lorsque vous raccordez plusieurs gestionnaires d’événements|
|[Avertissement du compilateur (niveau 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'Attribute' : WARNING !! l’attribut peut provoquer une génération de code non valide : utilisation avec précaution|
|[Avertissement du compilateur (niveau 1) C4685](compiler-warning-level-1-c4685.md)|'> >' attendu, '>>' trouvé lors de l'analyse des paramètres du modèle|
|[Avertissement du compilateur (niveau 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|’type défini par l’utilisateur’ : changement de comportement possible, changement de la convention d’appel de retour UDT|
|[Avertissement du compilateur (erreur) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'classe' : une classe abstraite sealed ne peut pas implémenter une interface’interface'|
|[Avertissement du compilateur (niveau 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint' : la liste des contraintes contient un type privé d’assembly 'type'|
|Avertissement du compilateur (niveau 1) C4689|'% c' : caractère non pris en charge dans #pragma detect_mismatch ; #pragma ignorée|
|[Avertissement du compilateur (niveau 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (POP)] : plus de pop que de push|
|[Avertissement du compilateur (niveau 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type' : le type référencé était attendu dans l’assembly non référencé’fichier', le type défini dans l’unité de traduction actuelle est utilisé à la place|
|[Avertissement du compilateur (niveau 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'fonction' : la signature de membre non privée contient un type natif privé d'assembly 'type_natif'|
|[Avertissement du compilateur (niveau 1, erreur) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'classe' : une classe abstraite sealed ne peut pas avoir de membres d’instance’membre d’instance'|
|[Avertissement du compilateur (niveau 1, erreur) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'classe' : une classe abstraite sealed ne peut pas avoir de classe de base’base_class'|
|Avertissement du compilateur (niveau 1) C4695|#pragma execution_character_set : 'jeu de caractères’n’est pas un argument pris en charge : actuellement seul’UTF-8 'est pris en charge|
|Avertissement du compilateur (niveau 1) C4696|Option/ZBvalue1 hors limites ; « valeur2 » en supposant|
|[Avertissement du compilateur (niveaux 1 et 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|variable locale’name’non initialisée utilisée|
|[Avertissement du compilateur (niveau 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|variable locale potentiellement non initialisée’nom’utilisée|
|[Avertissement du compilateur (niveau 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|code inaccessible|
|[Avertissement du compilateur (niveau 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|variable de pointeur local potentiellement non initialisée'% s’utilisée|
|[Avertissement du compilateur (niveau 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|assignation dans une expression conditionnelle|
|[Avertissement du compilateur (niveau 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|opérateur virgule dans une expression d’index de tableau|
|[Avertissement du compilateur (niveau 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'fonction' : fonction non inline|
|[Avertissement du compilateur (niveau 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|fonction’Function’sélectionnée pour l’expansion Inline automatique|
|[Avertissement du compilateur (niveau 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|fonction’Function’marquée comme __forceinline non inline|
|[Avertissement du compilateur (niveau 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'fonction' : les chemins de contrôle ne retournent pas tous une valeur|
|[Avertissement du compilateur (niveau 1, erreur) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'fonction' : doit retourner une valeur|
|[Avertissement du compilateur (niveau 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'fonction' : récurrent sur tous les chemins d’accès de contrôle, la fonction provoque un dépassement de capacité de la pile Runtime|
|[Avertissement du compilateur (niveau 4) C4718](compiler-warning-level-4-c4718.md)|'Function Call' : un appel récurrent n’a pas d’effets secondaires, suppression|
|Avertissement du compilateur (niveau 1) C4719|Constante double trouvée quand Qfast a spécifié-utilisez’f’comme suffixe pour indiquer une précision unique|
|Avertissement du compilateur (niveau 2) C4720|rapports assembleur en ligne : 'message'|
|Avertissement du compilateur (niveau 1) C4721|'fonction' : non disponible comme intrinsèque|
|[Avertissement du compilateur (niveau 1) C4722](compiler-warning-level-1-c4722.md)|'fonction' : le destructeur ne retourne jamais, fuite de mémoire potentielle|
|[Avertissement du compilateur (niveau 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|Division potentielle par 0|
|[Avertissement du compilateur (niveau 3) C4724](compiler-warning-level-3-c4724.md)|modulo potentiel par 0|
|Avertissement du compilateur (niveau 3) C4725|l'instruction peut manquer de précision sur certains processeurs Pentium|
|[Avertissement du compilateur (niveau 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH nommé pch_file avec le même horodatage trouvé dans obj_file_1 et obj_file_2.  Utilisation du premier PCH.|
|Avertissement du compilateur (niveau 1) C4728|Option/yl-ignorée, car une référence PCH est requise|
|Avertissement du compilateur (niveau 4) C4729|fonction trop importante pour les avertissements bas‚s sur les graphes de flux|
|[Avertissement du compilateur (niveau 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md) Avertissement du compilateur (niveau 1) C4730|'main' : le mélange d' _m64 et d’expressions à virgule flottante peut entraîner un code incorrect|
|[Avertissement du compilateur (niveau 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointeur' : Registre de pointeur de frame’Register’modifié par le code assembleur inline|
|Avertissement du compilateur (niveau 1) C4732|l’intrinsèque'% s’n’est pas pris en charge dans cette architecture|
|[Avertissement du compilateur (niveau 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Assignation de Inline asm à’FS : 0 ' : gestionnaire non inscrit en tant que gestionnaire sécurisé|
|[Avertissement du compilateur (niveau 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|stockage de résultat flottant 32 bits en mémoire, perte possible de performances|
|[Avertissement du compilateur (niveau 1) C4739](compiler-warning-level-1-c4739.md)|la référence à la variable ’var’ dépasse la taille de son espace de stockage|
|[Avertissement du compilateur (niveau 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|l’entrée ou la sortie du code ASM Inline supprime l’optimisation globale|
|[Avertissement du compilateur (niveau 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var’a un alignement différent dans’fichier1 'et’fichier2 ' : nombre et nombre|
|[Avertissement du compilateur (niveau 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type’a une taille différente dans’fichier1 'et’fichier2 ' : nombre et octets|
|[Avertissement du compilateur (niveau 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var’a un type différent dans’fichier1 'et’fichier2 ' : 'type1 'et’type2 '|
|[Avertissement du compilateur C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|l’accès volatile de'*expression*'est soumis à/volatile : \<iso&#124;ms> Setting ; envisagez d’utiliser __iso_volatile_load fonctions intrinsèques/Store|
|[Avertissement du compilateur (niveau 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Appel de’EntryPoint’managé : le code managé ne peut pas être exécuté pendant le verrouillage du chargeur, y compris le point d’entrée de DLL et les appels atteints à partir du point d’entrée de DLL|
|Avertissement du compilateur (niveau 4) C4749|pris en charge de manière conditionnelle : OffsetOf appliqué au type de disposition non standard'*type*'|
|[Avertissement du compilateur (niveau 1) C4750](compiler-warning-level-1-c4750.md)|'identifier' : fonction with _alloca() inline dans une boucle|
|Avertissement du compilateur (niveau 4) C4751|/Arch : AVX ne s’applique pas aux extensions Intel (R) streaming SIMD qui se trouvent dans le module ASM Inline|
|Avertissement du compilateur (niveau 4) C4752|Intel (R) Advanced Vector Extensions trouvé ; envisagez d’utiliser/arch : AVX|
|[Avertissement du compilateur (niveau 4) C4754](compiler-warning-level-4-c4754.md)|Les règles de conversion pour les opérations arithmétiques dans la comparaison à% s (% d) signifient qu’une branche ne peut pas être exécutée. Cast'% s’en'% s' (ou un type similaire de% d octets).|
|Avertissement du compilateur C4755|Les règles de conversion pour les opérations arithmétiques dans la comparaison à% s (% d) signifient qu’une branche ne peut pas être exécutée dans une fonction Inline. Cast'% s’en'% s' (ou un type similaire de% d octets).|
|[Avertissement du compilateur (niveau 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|dépassement de capacité arithmétique constante|
|Avertissement du compilateur (niveau 4) C4757|l’indice est une valeur non signée importante, voulez-vous une constante négative ?|
|[Avertissement du compilateur (niveau 4) C4764](compiler-warning-level-4-c4764.md)|Impossible d’aligner les objets catch sur plus de 16 octets|
|Avertissement du compilateur (niveau 4) C4767|le nom de section'% s’comporte plus de 8 caractères et sera tronqué par l’éditeur de liens|
|Avertissement du compilateur (niveau 3) C4768|__declspec attributs avant la spécification de la liaison sont ignorés|
|Avertissement du compilateur C4770|enum partiellement validé'*Name*'utilisé en tant qu’index|
|Avertissement du compilateur C4771|Les limites doivent être créées à l’aide d’un pointeur simple ; Fonction intrinsèque MPX ignorée|
|[Avertissement du compilateur (niveau 1, erreur) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import référencé un type à partir d’une bibliothèque de types manquante ; 'missing_type’utilisé en tant qu’espace réservé|
|Avertissement du compilateur (niveau 4) C4774|'*String*' : la chaîne de format attendue dans l’argument *Number* n’est pas un littéral de chaîne|
|Avertissement du compilateur (niveau 3) C4775|extension non standard utilisée dans la chaîne de format'*String*'de la fonction'*Function*'|
|Avertissement du compilateur (niveau 1) C4776|'%*character*'n’est pas autorisé dans la chaîne de format de la fonction'*Function*'|
|Avertissement du compilateur (niveau 4) C4777|'*fonction*' : la chaîne de mise en forme'*chaîne*'requiert un argument de type'*type1*', mais le *numéro* d’argument variadiques a le type'*type2*'|
|Avertissement du compilateur (niveau 3) C4778|'*fonction*' : chaîne de format'*String*'non terminée|
|[Avertissement du compilateur (niveau 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identificateur' : l’identificateur a été tronqué en caractères’nombre'|
|[Avertissement du compilateur (niveau 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|la mémoire tampon 'identificateur' d'une taille de N octets sera dépassée ; M octets seront écrits en commençant à l'offset L|
|Avertissement du compilateur (niveau 2) C4792|fonction'% s’déclarée à l’aide de sysimport et référencée à partir du code natif ; bibliothèque d’importation requise pour la liaison|
|[Avertissement du compilateur (niveaux 1 et 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'fonction' : fonction compilée comme Native : \ n\t’raison'|
|[Avertissement du compilateur (niveau 1) C4794](compiler-warning-level-1-c4794.md)|segment de la variable de stockage local du thread'% s’modifié de'% s’en'% s'|
|[Avertissement du compilateur (niveau 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|la fonction’Function’n’a pas d’instruction EMMS|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Avertissements du compilateur C4000 - C5999](compiler-warnings-c4000-c5999.md)
