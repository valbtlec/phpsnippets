#SHORT OPEN TAGS



```php

//remplace echo
<?= $afficheToi ?>

<!-- exemple de foreach -->
<?php foreach ($msg as $key => $value): ?>
<p><span class="boldtxt">Objet : </span><?= $value['objet']; ?></p>
<?php endforeach ?>

<!-- exemple de if -->
<?php if ($a == 5): ?>
...
<?php endif; ?>

<!-- exemple de switch -->

ATTENTION : Tout affichage (y compris d'espaces) entre une structure switch et le premier case va produire une erreur de syntaxe. Par exemple, ceci n'est pas valide :
<?php switch ($foo): ?>
    <?php case 1: ?>
    ...
<?php endswitch ?>
VALIDE :
<?php switch ($foo): ?>
<?php case 1: ?>
    ...
<?php endswitch ?>
```

