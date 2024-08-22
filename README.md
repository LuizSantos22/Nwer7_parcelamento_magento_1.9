ESTE É UM MÓDULO DE PARCELAMENTO DESENVOLVIDO PELA NEWER7 E AINDA ESTÁ SOB TESTES PARA TORNÁ-LO COMPATÍVEL COM MAGENTO 1.9/OPENMAGE 1.9X

Abra o arquivo view.phtml do seu tema (app/design/frontend/default/seu-tema/template/catalog/product/view.phtml)

Próximo a linha 100 (ou próximo das que chamam os preços no seu tema, no tema "Ultimo" por exemplo, vá em: 
app/design/frontend/ultimo/default/template/catalog/product/view.phtml  
É para inserir logo abaixo de dos seguintes trechos:
"<?php echo $this->getChildHtml('product_type_data'); ?>
						<?php if($_product->isSaleable()): ?>" , 

"<input type="hidden" name="related_product" id="related-products-field" value="" />
				</div>
				<?php if($_product->isSaleable()): ?>" 

e 

"<?php if ($_product->isSaleable() && $this->hasOptions()): ?>
			<?php if ($container1_html = $this->getChildChildHtml('container1', '', true, true)): ?>" 

Insira o código abaixo:

"<style type="text/css">
#parcelamento{clear:both;padding-top:8px;}
</style>

<?php if($_product->getTypeId() == 'configurable' && Mage::getStoreConfig('parcelamento/parcelamento_general/enabled')): ?>
<?php echo $this->getChildHtml("valores"); ?>
<?php endif; ?>" 

Pode realizar os ajustes se necessários, remover a citação de CSS no phtml, fazer um "wrap" e usar o CSS do site para editar
mencionando o wrap desse trecho, para estilizar corretamente. 
