                # loop-option-values-with-variant-id
                {% for option in product.options_with_values %}
                    <span>{{ option.name }}</span>
                    {% for value in option.values %}
                        {%- if product.options.size == 1 -%}
                         {%- if product.variants[forloop.index0].image -%}{%- assign variant_image = product.variants[forloop.index0].image -%}{%- endif -%}
                        {%- endif -%}
                    <a href="#" style="background-color: {{ value | lowercase | replace: ' ', '' }}; background-image: url({{ variant_image | img_url }})"></a>
                    {% endfor %}
                {% endfor %}


            $(document).ready(function() {
              $(document).on('click', '.productgrid--item .form-options-first .option-value .option-value-label:not(.disabled)',function() {
                var selectedval = $(this).find('.option-value-input').attr('data-value');
                $(this).parents('.productgrid--item').find('select.form-options').val(selectedval);
              });
            });
