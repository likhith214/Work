# Execute JavaScript to set the value
driver.execute_script("document.getElementById('form_input_custom_dropdown_model-package').value = 'Paquete A Chasis Cabina';")

# Optionally, trigger any events if necessary
driver.execute_script("document.getElementById('form_input_custom_dropdown_model-package').dispatchEvent(new Event('input'));")
