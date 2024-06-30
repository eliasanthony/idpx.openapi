openapi: 3.0.0
info:
  title: Identity Provider API
  version: 1.0.0
paths:
  /api/v2/auth/check_mail:
    post:
      tags:
        - Auth
      description: Check if an email is unique or in use
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/VerifiedEmailAddressDto'
      responses:
        '201':
          description: Get permissions
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/VerifiedEmailAddressDto'
components:
  schemas:
    VerifiedEmailAddressDto:
      type: object
      properties:
        _type:
          type: string
        email:
          type: string
          description: A user's email
        reset:
          type: boolean
        passwordRules:
          type: object
          properties:
            minLength:
              type: number
            maxLength:
              type: number
            minRequiredUppercase:
              type: number
            minRequiredLowerCase:
              type: number
            minRequiredSymbols:
              type: number
      example:
        _type: VerifiedEmailAddressDto
        email: pablo+test_pab001@alunacare.com
        reset: false
        passwordRules:
          minLength: 8
          maxLength: 25
          minRequiredUppercase: 1
          minRequiredLowerCase: 1
          minRequiredSymbols: 0
