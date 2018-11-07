# Phalcon #

## PHP > Phalcon

----
### How to output JSON from a controller action  ###

    <?php
        ...
        public function endpointAction()
        {
            $someOutputArray = ['hello', 'worlld'];
            // disable the view
            $this->view->disable();
            $this->response->setContentType('application/json', 'UTF-8');
            echo json_encode([1, 2, 3]);
        }
    ?>
