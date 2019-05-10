---
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
- C4728"
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
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 3df17b115797f4d68621854d072c41aca14a0fd8
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857563"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Avertissements du compilateur C4600 à C4799

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Warning|Message|
|-------------|-------------|
|[Avertissement du compilateur (niveau 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma 'macro name': expected a valid non-empty string|
|[Avertissement du compilateur (niveau 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro : 'nom de macro' pas de #pragma push_macro défini au préalable pour cet identificateur|
|[Avertissement du compilateur (niveau 1) C4603](compiler-warning-level-1-c4603.md)|«*identificateur*' : macro n’est pas définie ou la définition est différente après utilisation d’un en-tête précompilé|
|Avertissement du compilateur (niveau 1) C4604|«*type*» : passage d’argument par valeur sur une frontière native / managée nécessite un constructeur de copie valide. Sinon, le comportement d’exécution n’est pas défini|
|Avertissement du compilateur (niveau 1) C4605|' /D*macro*' spécifié sur la ligne de commande actuelle, mais n’a pas été spécifié lorsque l’en-tête précompilé a été généré|
|[Avertissement du compilateur (niveau 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma warning : 'numéro d’avertissement ignorée ; Avertissements d’analyse du code ne sont pas associés à des niveaux d’avertissement|
|[Avertissement du compilateur (niveau 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' a déjà été initialisé par un autre membre union dans la liste des initialiseurs, 'union_member'|
|Avertissement du compilateur (niveau 3, erreur) C4609|«*type1*'dérive d’interface par défaut'*interface*'sur le type'*type2*». Utiliser une autre interface par défaut pour '*type1*», ou une rupture de la relation de dérivation.|
|[Avertissement du compilateur (niveau 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|objet 'class' ne peut jamais être instancié - constructeur requis défini par l’utilisateur|
|[Avertissement du compilateur (niveau 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interaction entre 'fonction' et la destruction d’objets C++ n’est pas portable|
|[Avertissement du compilateur (niveau 1) C4612](compiler-warning-level-1-c4612.md)|erreur dans le nom de fichier Include|
|[Avertissement du compilateur (niveau 1) C4613](compiler-warning-level-1-c4613.md)|«*symbole*' : classe d’un segment ne peut pas être modifié.|
|[Avertissement du compilateur (niveau 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma warning : type d’avertissement utilisateur inconnu|
|[Avertissement du compilateur (niveau 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma warning : numéro d’avertissement 'number' pas un avertissement de compilateur valide|
|[Avertissement du compilateur (niveau 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|les paramètres pragma comportaient une chaîne vide. pragma ignoré|
|[Avertissement du compilateur (niveau 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning : numéro d'avertissement inexistant 'numéro'|
|[Avertissement du compilateur (niveau 1) C4620](compiler-warning-level-1-c4620.md)|aucune forme suffixée de l’opérateur 'operator ++' trouvée pour le type 'type' ; utilisez la forme préfixée|
|[Avertissement du compilateur (niveau 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|aucune forme suffixée de l’opérateur 'operator--' trouvée pour le type 'type', utilisez la forme préfixée|
|[Avertissement du compilateur (niveau 3) C4622](compiler-warning-level-3-c4622.md)|remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'|
|[Avertissement du compilateur (niveau 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'classe dérivée' : constructeur par défaut a été défini de manière implicite comme supprimé car un constructeur par défaut de la classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'classe dérivée' : destructeur a été défini de manière implicite comme supprimé car un destructeur de classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'classe dérivée' : constructeur de copie a été défini de manière implicite comme supprimé car un constructeur de copie de la classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'classe dérivée' : opérateur d’assignation a été défini de manière implicite comme supprimé car un opérateur d’assignation de classe de base est inaccessible ou supprimé|
|[Avertissement du compilateur (niveau 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<identificateur >': ignoré lors de la recherche une utilisation d’en-tête précompilé|
|[Avertissement du compilateur (niveau 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|digrammes non pris en charge avec -Ze. Séquence de caractères 'digramme' non interprétée comme jeton de remplacement pour « %s »|
|[Avertissement du compilateur (niveau 4) C4629](compiler-warning-level-4-c4629.md)|digrammes utilisés, séquence de caractères 'digramme' interprétée comme jeton 'caractère' (insérez un espace entre les deux caractères si cela n’est pas ce que vous souhaitiez)|
|[Avertissement du compilateur (niveau 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbole' : spécificateur de classe de stockage 'extern' non conforme sur définition de membre|
|Avertissement du compilateur (niveau 2) C4631|MSXML ou XPath non disponible, les commentaires de document XML ne seront pas traités. raison|
|[Avertissement du compilateur (niveau 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Commentaire de document XML : fichier - accès refusé : raison|
|[Avertissement du compilateur (niveau 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Cible de commentaire de document XML : erreur : raison|
|[Avertissement du compilateur (niveau 4) C4634](compiler-warning-level-4-c4634.md)|Cible de commentaire de document XML : ne peut pas être appliqué : raison|
|[Avertissement du compilateur (niveau 3) C4635](compiler-warning-level-3-c4635.md)|Cible de commentaire de document XML : code XML incorrect : raison|
|[Avertissement du compilateur (niveau 3) C4636](compiler-warning-level-3-c4636.md)|Commentaire de document XML appliqué pour construire : la balise requiert non vide ' attribut '.|
|[Avertissement du compilateur (niveaux 3 et 4) C4637](compiler-warning-level-3-c4637.md)|Cible de commentaire de document XML : \<inclure > balise ignorée. Raison|
|[Avertissement du compilateur (niveau 3) C4638](compiler-warning-level-3-c4638.md)|Cible de commentaire de document XML : référence à un symbole inconnu 'symbol'.|
|[Avertissement du compilateur (niveau 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Erreur MSXML, document XML commentaires ne seront pas traités. Raison|
|[Avertissement du compilateur (niveau 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance' : la construction d'un objet static local n'est pas thread-safe|
|[Avertissement du compilateur (niveau 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Commentaire de document XML a une référence croisée ambiguë :|
|[Avertissement du compilateur (niveau 3) C4645](compiler-warning-level-3-c4645.md)|la fonction déclarée avec __declspec(noreturn) a une instruction return|
|[Avertissement du compilateur (niveau 3) C4646](compiler-warning-level-3-c4646.md)|la fonction déclarée avec __declspec(noreturn) a un type de retour non void|
|Avertissement du compilateur (niveau 3) C4647|changement de comportement : __is_pod (*type*) a une valeur différente dans les versions précédentes|
|Avertissement du compilateur (niveau 3) C4648|attribut standard 'carries_dependency' est ignoré|
|Avertissement du compilateur (niveau 3) C4649|les attributs sont ignorés dans ce contexte|
|[Avertissement du compilateur (niveau 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informations de débogage pas dans l’en-tête précompilé ; Seuls les symboles globaux de l’en-tête seront disponibles|
|[Avertissement du compilateur (niveau 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|« définition » spécifiée pour l’en-tête précompilé mais non pour la compilation actuelle|
|[Avertissement du compilateur (niveau 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|option du compilateur 'option' non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours se substituera à celle définie dans l’en-tête précompilé|
|[Avertissement du compilateur (niveau 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|option du compilateur 'option' non cohérente avec l’en-tête précompilé ; option de ligne de commande en cours ignorée|
|Avertissement du compilateur (niveau 4) C4654|Le code placé avant d’inclure d’en-tête précompilé ligne sera ignorée. Ajoutez le code à l’en-tête précompilé.|
|[Avertissement du compilateur (niveau 1) C4655](compiler-warning-level-1-c4655.md)|'symbole' : type de variable postérieur à la dernière génération, ou défini différemment à un autre emplacement|
|[Avertissement du compilateur (niveau 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbole' : type de données est nouveau ou a été modifié depuis la dernière build ou est défini différemment à un autre emplacement|
|[Avertissement du compilateur (niveau 1) C4657](compiler-warning-level-1-c4657.md)|l’expression implique un type de données qui sont nouvel depuis la dernière build|
|Avertissement du compilateur (niveau 1) C4658|'fonction' : prototype de fonction est postérieur à la build la plus récente, ou est déclaré différemment à un autre emplacement|
|[Avertissement du compilateur (niveau 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'pragma' : utilisation du segment réservé 'segment' a un comportement indéfini, utilisez #pragma comment (linker,...)|
|[Avertissement du compilateur (niveau 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identificateur' : aucune définition appropriée pour la demande d’instanciation explicite du modèle|
|[Avertissement du compilateur (niveau 1) C4662](compiler-warning-level-1-c4662.md)|instanciation explicite ; la classe de modèle 'identificateur1' n’a aucune définition pour spécialiser 'identificateur2'|
|[Avertissement du compilateur (niveau 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'fonction' : aucun modèle de fonction défini correspondant à l’instanciation n’imposée|
|[Avertissement du compilateur (niveau 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbole' n’est pas défini comme préprocesseur ou macro, remplacement par '0' pour la directive 'directive'|
|[Avertissement du compilateur (niveau 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast' : conversion risquée : 'classe' est un objet de type managé|
|[Avertissement du compilateur (niveau 4) C4670](compiler-warning-level-4-c4670.md)|'identificateur' : cette classe de base est inaccessible|
|Avertissement du compilateur (niveau 4) C4671|'identificateur' : le constructeur de copie est inaccessible|
|[Avertissement du compilateur (niveau 4) C4672](compiler-warning-level-4-c4672.md)|'identificateur1' : ambigu. Déjà rencontré comme 'identifier2'|
|[Avertissement du compilateur (niveau 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|lever des types suivants de 'identificateur' ne sera plus utilisé que sur le site catch|
|[Avertissement du compilateur (niveau 1) C4674](compiler-warning-level-1-c4674.md)|'method' doit être déclaré 'static' et avoir un seul paramètre|
|Avertissement du compilateur (niveau 4) C4676|« %s » : le destructeur n’est pas accessible|
|[Avertissement du compilateur (niveau 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'fonction' : signature de membre non privée contient un type privé d’assembly 'type_privé'|
|[Avertissement du compilateur (niveau 1) C4678](compiler-warning-level-1-c4678.md)|La classe de base 'base_type' est moins accessible que 'derived_type'|
|[Avertissement du compilateur (niveau 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'membre' : Impossible d’importer le membre|
|[Avertissement du compilateur (niveau 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class' : coclasse ne spécifie pas une interface par défaut|
|[Avertissement du compilateur (niveau 4) C4681](compiler-warning-level-4-c4681.md)|'class' : coclasse ne spécifie pas une interface par défaut qui est une source d’événement|
|[Avertissement du compilateur (niveau 4) C4682](compiler-warning-level-4-c4682.md)|'paramètre' : aucun attribut de paramètre directionnel spécifié, [in] pris par défaut|
|[Avertissement du compilateur (niveau 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'fonction' : source de l’événement a un 'out'-paramètre ; Soyez prudent lorsque vous raccordez plusieurs gestionnaires d’événements|
|[Avertissement du compilateur (niveau 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': AVERTISSEMENT !! attribut peut entraîner une génération de code non valide : utilisez avec précaution|
|[Avertissement du compilateur (niveau 1) C4685](compiler-warning-level-1-c4685.md)|'> >' attendu, '>>' trouvé lors de l'analyse des paramètres du modèle|
|[Avertissement du compilateur (niveau 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|’type défini par l’utilisateur’ : changement de comportement possible, changement de la convention d’appel de retour UDT|
|[Avertissement (erreur) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'classe' : une classe abstraite sealed ne peut pas implémenter une interface 'interface'|
|[Avertissement du compilateur (niveau 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint' : la liste des contraintes contient un type privé d’assembly 'type'|
|Avertissement du compilateur (niveau 1) C4689|'%c': unsupported character in #pragma detect_mismatch; #pragma ignored|
|[Avertissement du compilateur (niveau 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)] : plus de POP que de push|
|[Avertissement du compilateur (niveau 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type' : type référencé était attendu dans l’assembly non référencé 'fichier', type défini dans l’unité de traduction actuelle utilisée à la place|
|[Avertissement du compilateur (niveau 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'fonction' : la signature de membre non privée contient un type natif privé d'assembly 'type_natif'|
|[Avertissement du compilateur (niveau 1, erreur) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'classe' : une classe abstraite sealed ne peut pas avoir n’importe quelle instance membres 'instance member'|
|[Avertissement du compilateur (niveau 1, erreur) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'classe' : une classe abstraite sealed ne peut pas avoir une classe de base 'base_class'|
|Avertissement du compilateur (niveau 1) C4695|#pragma execution_character_set : jeu de caractères' n’est pas un argument prises en charge : actuellement, seul « UTF-8' est pris en charge|
|Avertissement du compilateur (niveau 1) C4696|/ Option ZBvalue1 hors limites ; en supposant que 'value2'|
|[Avertissement du compilateur (niveaux 1 et 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|variable locale non initialisée 'name' utilisé|
|[Avertissement du compilateur (niveau 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|variable locale potentiellement non initialisée 'name' utilisé|
|[Avertissement du compilateur (niveau 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|code inaccessible|
|[Avertissement du compilateur (niveau 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|variable de pointeur locale potentiellement non initialisée utilisée « %s »|
|[Avertissement du compilateur (niveau 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|assignation au sein d’une expression conditionnelle|
|[Avertissement du compilateur (niveau 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|opérateur virgule au sein de l’expression d’index de tableau|
|[Avertissement du compilateur (niveau 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'fonction' : fonction non inline|
|[Avertissement du compilateur (niveau 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|' fonction ' sélectionnée pour expansion inline automatique|
|[Avertissement du compilateur (niveau 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|' fonction ' marquée comme __forceinline non inline|
|[Avertissement du compilateur (niveau 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'fonction' : pas de tous les chemins de contrôle retournent une valeur|
|[Avertissement du compilateur (niveau 1, erreur) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'fonction' : doit retourner une valeur|
|[Avertissement du compilateur (niveau 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'fonction' : récurrent sur tous les chemins d’accès de contrôle, la fonction entraînera un débordement de pile d’exécution|
|[Avertissement du compilateur (niveau 4) C4718](compiler-warning-level-4-c4718.md)|'function call' : appel récurrent n’a pas d’effets secondaires, suppression|
|Avertissement du compilateur (niveau 1) C4719|Constante double trouvée avec Qfast spécifié - utilisez 'f' comme suffixe pour indiquer simple précision|
|Avertissement du compilateur (niveau 2) C4720|dans assembleur inline signale : 'message'|
|Avertissement du compilateur (niveau 1) C4721|'fonction' : non disponible comme intrinsèque|
|[Avertissement du compilateur (niveau 1) C4722](compiler-warning-level-1-c4722.md)|'fonction' : aucun retour du destructeur, fuite de mémoire|
|[Avertissement du compilateur (niveau 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|division potentielle par 0|
|[Avertissement du compilateur (niveau 3) C4724](compiler-warning-level-3-c4724.md)|modulo potentiel par 0|
|Avertissement du compilateur (niveau 3) C4725|l'instruction peut manquer de précision sur certains processeurs Pentium|
|[Avertissement du compilateur (niveau 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH nommé fichier_pch comportant le même horodatage dans fichier_obj_1 et fichier_obj_2.  À l’aide du premier PCH.|
|Avertissement du compilateur (niveau 1) C4728|/ Option Yl-ignorée, car une référence PCH est requise|
|Avertissement du compilateur (niveau 4) C4729|fonction trop importante pour les avertissements bas‚s sur les graphes de flux|
|[Avertissement (niveau 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)Avertissement du compilateur (niveau 1) C4730|« principal » : combinaison de _m64 et expressions peuvent entraîner un code erroné de virgule flottante|
|[Avertissement (niveau 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointeur' : Registre de pointeur 'Registre' modifié par le code assembleur inline frame|
|Avertissement du compilateur (niveau 1) C4732|intrinsèque « %s » n’est pas pris en charge dans cette architecture|
|[Avertissement (niveau 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Affectation de inline asm à 'FS : 0' : gestionnaire non inscrit en tant que gestionnaire safe|
|[Avertissement (niveau 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|stockage de résultat flottant 32 bits en mémoire, perte possible de performances|
|[Avertissement du compilateur (niveau 1) C4739](compiler-warning-level-1-c4739.md)|la référence à la variable ’var’ dépasse la taille de son espace de stockage|
|[Avertissement (niveau 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|flux entrant ou sortant code asm incorporé supprime l’optimisation globale|
|[Avertissement (niveau 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' a un alignement différent dans 'fichier1' et 'fichier2' : nombre et nombre|
|[Avertissement (niveau 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' a une taille différente dans 'fichier1' et 'fichier2' : nombre et le nombre d’octets|
|[Avertissement (niveau 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' a un type différent dans 'fichier1' et 'fichier2' : 'type1' et 'type2'|
|[Avertissement C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|accès volatile de «*expression*' volatile :\<iso&#124;ms > configuration ; envisagez d’utiliser des fonctions intrinsèques __iso_volatile_load/store|
|[Avertissement du compilateur (niveau 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Appel géré 'point d’entrée' : Impossible d’exécuter du code managé le verrouillage du chargeur, y compris le point d’entrée DLL et les appels accessibles à partir du point d’entrée DLL|
|Avertissement du compilateur (niveau 4) C4749|prise en charge conditionnelle : offsetof appliqué au type de connexion non standard-disposition '*type*'|
|[Avertissement du compilateur (niveau 1) C4750](compiler-warning-level-1-c4750.md)|'identifier' : fonction with _alloca() inline dans une boucle|
|Avertissement du compilateur (niveau 4) C4751|/ arch : AVX ne s’applique pas à Intel (r) Extensions Streaming SIMD situés au sein d’inline ASM|
|Avertissement du compilateur (niveau 4) C4752|trouvé Intel (r) Advanced Vector Extensions ; envisagez d’utiliser/arch : AVX|
|[Avertissement du compilateur (niveau 4) C4754](compiler-warning-level-4-c4754.md)|Les règles de conversion pour les opérations arithmétiques dans la comparaison à %s(%d) signifient qu’une branche ne peut pas être exécutée. Effectuer un cast de « %s » à « %s » (ou un type similaire de %d octets).|
|Avertissement C4755 du compilateur|Les règles de conversion pour les opérations arithmétiques dans la comparaison à %s(%d) signifient qu’une branche ne peut pas être exécutée dans une fonction inline. Effectuer un cast de « %s » à « %s » (ou un type similaire de %d octets).|
|[Avertissement du compilateur (niveau 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|dépassement de capacité dans une opération arithmétique de constante|
|Avertissement du compilateur (niveau 4) C4757|indice est une valeur non signée élevée, souhaitiez-vous une constante négative ?|
|[Avertissement du compilateur (niveau 4) C4764](compiler-warning-level-4-c4764.md)|Impossible d’aligner les objets de bloc catch sur plus de 16 octets|
|Avertissement du compilateur (niveau 4) C4767|nom de la section « %s » est supérieure à 8 caractères et sera tronqué par l’éditeur de liens|
|Avertissement du compilateur (niveau 3) C4768|attributs __declspec avant la spécification de liaison sont ignorés.|
|Avertissement C4770 du compilateur|enum partiellement validé '*nom*» utilisé en tant qu’index|
|Avertissement C4771 du compilateur|Limites doivent être créés à l’aide d’un simple pointeur ; Fonction intrinsèque MPX sera ignorée|
|[Avertissement du compilateur (niveau 1, erreur) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import a référencé un type à partir d’une bibliothèque de types manquante ; 'type_manquant' utilisé comme espace réservé|
|Avertissement du compilateur (niveau 4) C4774|«*chaîne*' : chaîne attendue dans l’argument de format *nombre* n’est pas une chaîne littérale|
|Avertissement du compilateur (niveau 3) C4775|extension non standard utilisée dans la chaîne de format «*chaîne*'de la fonction'*fonction*'|
|Avertissement du compilateur (niveau 1) C4776|' %*caractère*'n’est pas autorisée dans la chaîne de format de la fonction'*fonction*'|
|Avertissement du compilateur (niveau 4) C4777|'*fonction*' : chaîne de format '*chaîne*'requiert un argument de type'*type1*', mais l’argument variadique *nombre* a le type '*type2*'|
|Avertissement du compilateur (niveau 3) C4778|«*fonction*' : chaîne de format indéterminée '*chaîne*»|
|[Avertissement (niveau 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identificateur' : identificateur tronqué à 'nombre' caractères|
|[Avertissement (niveau 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|la mémoire tampon 'identificateur' d'une taille de N octets sera dépassée ; M octets seront écrits en commençant à l'offset L|
|Avertissement du compilateur (niveau 2) C4792|la fonction « %s » déclarée à l’aide de sysimport et référencée à partir de code natif ; obligé pour lier la bibliothèque d’importation|
|[Avertissement du compilateur (niveau 1 et 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'fonction' : fonction compilée en tant que natif : \n\t'reason'|
|[Avertissement du compilateur (niveau 1) C4794](compiler-warning-level-1-c4794.md)|segment du stockage local des threads variable « %s » a été remplacée par « %s » à « %s »|
|[Avertissement du compilateur (niveau 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|fonction 'fonction' n’a aucune instruction EMMS|

## <a name="see-also"></a>Voir aussi

[C /C++ compilateur et build erreurs et avertissements des outils](../compiler-errors-1/c-cpp-build-errors.md) \
[Avertissements du compilateur C4000 - C5999](compiler-warnings-c4000-c5999.md)
